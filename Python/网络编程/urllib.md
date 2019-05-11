前言：
在能使用的各种网络工作库中，功能最强大的是urllib和URLlib2，它们能让通过网络访问文件，就像那些文件存在你的电脑上一样。通过简单的调用函数，几乎可以把所有指向的东西用做程序的输入。
如果只是下载，urllib就可以了，如果使用HTTP验证，或cookie验证或者要为自己的协议写扩展程序话，urllib2是一个好的选择。
## 打开远程文件
可以像打开本地文件一样打开远程文件，不同之处在于是可以使用只读模式，使用的是来自urllib模块的urlopen，而不是open。
URLopen返回的类文件类型支持close，read，readline和readlines方法，当然也支持迭代表达式来实现
## 获取远程文件
函数urlopen提供一个能从中读取数据的类文件对象。如果希望urllib为你下载文件并在本地文件中存储一个文件的副本，那么可以使用urlretrive返回一个元组（filename，headers）而不是类文件对象，filename是本地对象的名字，headers包含一些远程文件的信息
`urlretrieve('http://baidu.com','C:\\python.html')`
## 附录
包含的模块
- urllib.request：Opening and reading URLS
- urllib.error：
- urllib.parse：for parsing URLs
- urlllib.robotpares：for parsing robots.txt files。
```py
url = 'https://tinypng.com/images/social/website.jpg'

def testRequest():
    image_name = 'test1.jpg'
    r = requests.get(url, stream=True)
    with open(image_name, 'wb') as f:
        for chunk in r.iter_content():
            f.write(chunk)

def testRequest2():
    image_name = 'test2.jpg'
    r = requests.get(url)
    i = Image.open(StringIO(r.content))
    i.save(image_name)

def testUrllib():
    image_name = 'test3.jpg'
    testfile = urllib.URLopener()
    testfile.retrieve(url, image_name)

def testwget():
    image_name = 'test4.jpg'
    wget.download(url, image_name)

if __name__ == '__main__':
    profile.run('testRequest()')
    profile.run('testRequest2()')
    profile.run('testUrllib()')
    profile.run('testwget()')
```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyNDI4NjYyN119
-->