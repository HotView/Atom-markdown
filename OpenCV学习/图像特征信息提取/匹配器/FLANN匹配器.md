## FLANN匹配
Fast Library for Approximate Nearest Neighbors : 近似最近邻的快速库
#### 针对SIFT和SURF的参数设置
flann = cv2.FlannBasedMatcher(indexParams,searchParams)
参数：索引类型
- indexParams = dict(algorithm = FLANN_INDEX_KDTREE,trees = 5)
所构造的索引将由一组随机的kd-tree组成，这些kd-tree将并行搜索。
- trees：要使用的并行kd树的数目。好值位于[1..16]范围内。


参数：搜索的类型
- searchParams = dict(check=50)
索引中树的递归遍历次数。该参数值越高，搜索精度越好，但也需要更多的时间。如果在创建索引时使用自动配置，还会计算达到指定精度所需的检查次数，在这种情况下忽略该参数
#### 针对ORB二值描述符的参数设置
创建的索引使用多探针LSH
```c
struct LshIndexParams : public IndexParams
{
LshIndexParams(
unsigned int table_number,
unsigned int key_size,
unsigned int multi_probe_level );
};
```
- table_number：要使用的哈希表的数量(通常在10到30之间)。
- key_size：哈希键的大小以位为单位(通常在10到20之间)。
- multi_probe_level：要移动的位数来检查相邻的桶(0是常规的LSH，建议是2)

示例
```py
index_params = dict(algorithm = FLANN_INDEX_LSH,
    table_number = 6, # 12
    key_size = 12,  # 20
    multi_probe_level = 1)
    search_params = dict(checks=50)
    # or pass empty dictionary

fbm = cv2.FlannBasedMatcher(index_params,
            search_params)
matches = fbm.knnMatch(des1,des2,k=2)
```
## 附录
LSH(Locality Sensitive Hashing)翻译成中文，叫做“局部敏感哈希”，它是一种针对海量高维数据的快速最近邻查找算法。

在信息检索，数据挖掘以及推荐系统等应用中，我们经常会遇到的一个问题就是面临着海量的高维数据，查找最近邻。如果使用线性查找，那么对于低维数据效率尚可，而对于高维数据，就显得非常耗时了。为了解决这样的问题，人们设计了一种特殊的hash函数，使得2个相似度很高的数据以较高的概率映射成同一个hash值，而令2个相似度很低的数据以极低的概率映射成同一个hash值。我们把这样的函数，叫做LSH（局部敏感哈希）。LSH最根本的作用，就是能高效处理海量高维数据的最近邻问题

FLANN的单应性问题
单应性就是一个条件：当两幅图像中的一幅出现投影畸变（perspective distortion）时，它们还能彼此匹配。
