# 算法实现：(详细见代码文档) #

# 双数之和的一个查找，只实现了最简单的方式，但是，哈希表的解决方案还未完善，没有解决哈希冲突。 #

# 复盘 #

1. 如果两个循环，先循环保存到字典，再循环查找字典里面的键-值
 困局：哈希冲突，不能把相同的值保存为两个不同的键

2. 一个循环
	-   把列表的元素按(元素：索引)存储到字典里时，用目标值target去减下一个要存储的列表元素得到寻找值temp，再找字典里有没有与temp值相同的键，有的话，输出这个键对应的值和下一个要存储的列表的索引。
	(用下一个列表元素产生的差值找字典中存储的列表)
	- 把target与列表元素的差值按(差值：该元素索引)存储到字典里，再用下一个要存储的列表元素查找字典，如果有，说明存在另一个列表元素和这个要存储的列表元素相加得到目标值，输出查找到的字典差值中的索引和下一个要存储的列表元素的索引
	(用下一个列表元素找字典中存储的列表元素产生的差值)

以上两种方法的重点在于，先判断后存储，避免了字典中同时存在要拿来比较的元素，自己比较自己的情况，也避免了哈希冲突，因为即便是由列表中两个相同元素相加得到目标值，也在将列表存储到字典之前，也即产生哈希冲突之前已经判断完成输出了。
