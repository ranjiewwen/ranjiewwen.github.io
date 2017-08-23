---
layout: post
title: 侯捷STL学习（十）
date: 2017-07-23
tag: 侯捷STL
---

## 第二十三节 容器hashtable探索

- hashtable冲突（碰撞）处理
- rehash时，篮子扩充两倍，找到其附近的质数，重新计算元素位置
- 内部扩充的数据已经预定好，53->97->....
![](http://i.imgur.com/hmr8BBN.png)
- hashtable实现
- iterator要实现当当前node链表结束，要能进入到下一个buckets
![](http://i.imgur.com/mQVDkfO.png)
- hashtable使用
- 模板参数的形式
![](http://i.imgur.com/XEFQdQH.png)
- 容器hashtable中hashfunction
- hash{}的偏特化实现
![](http://i.imgur.com/jiPG8li.png)
- hashtable使用
![](http://i.imgur.com/vWUgBOf.png)

## C++11--unordered容器

- 结构
![](http://i.imgur.com/bysnHyH.png)
- test unordered_set
```C++
#include <unordered_set>
#include <stdexcept>
#include <string>
#include <cstdlib> //abort()
#include <cstdio>  //snprintf()
#include <iostream>
#include <ctime> 
namespace jj15
{
void test_unordered_set(long& value)
{
	cout << "\ntest_unordered_set().......... \n";
     
unordered_set<string> c;  	
char buf[10];
			
clock_t timeStart = clock();								
    for(long i=0; i< value; ++i)
    {
    	try {
    		snprintf(buf, 10, "%d", rand());
        	c.insert(string(buf));    			 		
		}
		catch(exception& p) {
			cout << "i=" << i << " " << p.what() << endl;	
			abort();
		}
	}
	cout << "milli-seconds : " << (clock()-timeStart) << endl;		
	cout << "unordered_set.size()= " << c.size() << endl;	
	cout << "unordered_set.max_size()= " << c.max_size() << endl;  //357913941
	cout << "unordered_set.bucket_count()= " << c.bucket_count() << endl;	
	cout << "unordered_set.load_factor()= " << c.load_factor() << endl;	
	cout << "unordered_set.max_load_factor()= " << c.max_load_factor() << endl;	
	cout << "unordered_set.max_bucket_count()= " << c.max_bucket_count() << endl;			
  	for (unsigned i=0; i< 20; ++i) {
    	cout << "bucket #" << i << " has " << c.bucket_size(i) << " elements.\n";
  	}			
	
string target = get_a_target_string();	
	{
    timeStart = clock();
auto pItem = find(c.begin(), c.end(), target);	//比 c.find(...) 慢很多	
	cout << "std::find(), milli-seconds : " << (clock()-timeStart) << endl;		
	if (pItem != c.end())
    	cout << "found, " << *pItem << endl;
  	else
    	cout << "not found! " << endl;	
 	}
 
 	{
    timeStart = clock();		
auto pItem = c.find(target);		//比 std::find(...) 快很多							
	cout << "c.find(), milli-seconds : " << (clock()-timeStart) << endl;		 
	if (pItem != c.end())
    	cout << "found, " << *pItem << endl;
  	else
    	cout << "not found! " << endl;	
 	}	
}															 
}

```