Git版本库的对象数据库中，我们可以看到11个对象：
- 4个数据对象，
- 3个数对象，
- 3个提交对象和1个标签对象。
## `git verify-pack`
这个底层命令用来查看已经打包的内容。
## 打包数据的过程
Git 使用 zlib 压缩这些文件的内容，而且我们并没有存储太多东西，所以上文中的文件一共只占用了 925 字节。 接下来，我们会指引你添加一些大文件到版本库中，以此展示 Git 的一个很有趣的功能。 为了便于展示，我们要把之前在 Grit 库中用到过的  `repo.rb`  文件添加进来——这是一个大小约为 22K 的源代码文件：

```console
$ curl https://raw.githubusercontent.com/mojombo/grit/master/lib/grit/repo.rb > repo.rb
$ git add repo.rb
$ git commit -m 'added repo.rb'
[master 484a592] added repo.rb
 3 files changed, 709 insertions(+), 2 deletions(-)
 delete mode 100644 bak/test.txt
 create mode 100644 repo.rb
 rewrite test.txt (100%)
```

如果你查看生成的树对象，可以看到 repo.rb 文件对应的数据对象的 SHA-1 值：

```console
$ git cat-file -p master^{tree}
100644 blob fa49b077972391ad58037050f2a75f74e3671e92      new.txt
100644 blob 033b4468fa6b2a9547a70d88d1bbe8bf3f9ed0d5      repo.rb
100644 blob e3f094f522629ae358806b17daf78246c27c007b      test.txt
```

接下来你可以使用  `git cat-file`  命令查看这个对象有多大：

```console
$ git cat-file -s 033b4468fa6b2a9547a70d88d1bbe8bf3f9ed0d5
22044
```

现在，稍微修改这个文件，然后看看会发生什么：

```console
$ echo '# testing' >> repo.rb
$ git commit -am 'modified repo a bit'
[master 2431da6] modified repo.rb a bit
 1 file changed, 1 insertion(+)
```

查看这个提交生成的树对象，你会看到一些有趣的东西：

```console
$ git cat-file -p master^{tree}
100644 blob fa49b077972391ad58037050f2a75f74e3671e92      new.txt
100644 blob b042a60ef7dff760008df33cee372b945b6e884e      repo.rb
100644 blob e3f094f522629ae358806b17daf78246c27c007b      test.txt
```

repo.rb 对应一个与之前完全不同的数据对象，这意味着，虽然你只是在一个 400 行的文件后面加入一行新内容，Git 也会用一个全新的对象来存储新的文件内容：

```console
$ git cat-file -s b042a60ef7dff760008df33cee372b945b6e884e
22054
```

你的磁盘上现在有两个几乎完全相同、大小均为 22K 的对象。 如果 Git 只完整保存其中一个，再保存另一个对象与之前版本的差异内容，岂不更好？

事实上 Git 可以那样做。 Git 最初向磁盘中存储对象时所使用的格式被称为“松散（loose）”对象格式。 但是，Git 会时不时地将多个这些对象打包成一个称为“包文件（packfile）”的二进制文件，以节省空间和提高效率。 当版本库中有太多的松散对象，或者你手动执行  `git gc`  命令，或者你向远程服务器执行推送时，Git 都会这样做。 要看到打包过程，你可以手动执行  `git gc`  命令让 Git 对对象进行打包：

```console
$ git gc
Counting objects: 18, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (14/14), done.
Writing objects: 100% (18/18), done.
Total 18 (delta 3), reused 0 (delta 0)
```

这个时候再查看 objects 目录，你会发现大部分的对象都不见了，与此同时出现了一对新文件：

```console
$ find .git/objects -type f
.git/objects/bd/9dbf5aae1a3862dd1526723246b20206e5fc37
.git/objects/d6/70460b4b4aece5915caf5c68d12f560a9fe3e4
.git/objects/info/packs
.git/objects/pack/pack-978e03944f5c581011e6998cd0e9e30000905586.idx
.git/objects/pack/pack-978e03944f5c581011e6998cd0e9e30000905586.pack
```

仍保留着的几个对象是未被任何提交记录引用的数据对象——在此例中是你之前创建的“what is up, doc?”和“test content”这两个示例数据对象。 因为你从没将它们添加至任何提交记录中，所以 Git 认为它们是悬空（dangling）的，不会将它们打包进新生成的包文件中。

剩下的文件是新创建的包文件和一个索引。 包文件包含了刚才从文件系统中移除的所有对象的内容。 索引文件包含了包文件的偏移信息，我们通过索引文件就可以快速定位任意一个指定对象。 有意思的是运行  `gc`命令前磁盘上的对象大小约为 22K，而这个新生成的包文件大小仅有 7K。 通过打包对象减少了 ⅔ 的磁盘占用空间。

Git 是如何做到这点的？ Git 打包对象时，会查找命名及大小相近的文件，并只保存文件不同版本之间的差异内容。 你可以查看包文件，观察它是如何节省空间的。  `git verify-pack`  这个底层命令可以让你查看已打包的内容：

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTMxMzI5MF19
-->