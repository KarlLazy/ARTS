# 1. Algorithm

- 26 .  删除排序数组的重复项  

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。  
不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。  
  
  
```

class Solution {
	public int removeDuplicates(int[] nums) {
		int temp = 0;
		int t1 = 0;
		for (int i = 0; i < nums.length;) {
			t1 = i;
			nums[temp] = nums[i];
			temp++;
			for (int j = i + 1; j < nums.length; j++) {
				if (nums[j] != nums[i]) {
					i = j;
					break;
				}
			}
			if (t1 == i)
				break;
		}
		return temp;
	}
}
```

手法还是很稚嫩，想的也不是很清楚。之后要先把思路写出来，再去实现。  


```
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
}

```
用双指针的方法，快指针j，慢指针i，对应的值相等时，就增加j以跳过重复项，不等时就把nums[j]赋值到nums[i+1]，然后递增i。  

- 26 .  买卖股票的最佳时机  

给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。  
设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。  
注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）  

```
class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length < 0)
            return 0;
        int sum=0;
        for(int i=1;i<prices.length;i++){
            if(prices[i] - prices[i-1] > 0)
                sum+=prices[i] - prices[i-1];
        }
        return sum;
    }
}

```
用双指针的方法，快指针j，慢指针i，对应的值相等时，就增加j以跳过重复项，不等时就把nums[j]赋值到nums[i+1]，然后递增i。

# 2. Review
英文文档也看了些，不过我的阅读能力还是不够，好多地方都没看懂，也没怎么找到适合初学者看的文章。  
接下来会多看些短篇和论坛，现在暂时就先分享中文的文章  
[http传输原理](https://www.cnblogs.com/chenliyang/p/6558756.html),这个对http介绍的也算蛮详细的，比较适合入门吧。  
  
# 3. Tip
记录下最近常用的工具快捷键，主要是eclipse，虽然以前也有用过，不过只知道要怎么用，现在想汇总一下。  
  
首先是调试：  
F5：Step Into（debug）进入当前行的方法内部,一步一步执行；  
F6：Step over（debug）执行当前行,但不进入执行细节；  
F7：Step return（debug）返回上一步执行的方法（相对应F5）；  
F8：Resume（debug）恢复执行,表示接着执行代码,直接跳到下一个断点；  
  
然后是一些零碎的：  
crtl+shift+P：匹配大括号；  
crtl+shift+F：格式化代码；  
crtl+shift+R：打开资源；  

# 4. Share
原文看不懂，只能先看些别人啃过的东西。  
[V神论文摘要](https://mp.weixin.qq.com/s/UPZRVPfu2wNFDCQSbk1Lgg)
