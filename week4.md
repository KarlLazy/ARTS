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
用双指针的方法，快指针j，慢指针i，  
对应的值相等时，就增加j以跳过重复项，不等时就把nums[j]赋值到nums[i+1]，然后递增i。  

- 122 .  买卖股票的最佳时机  

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
有些东西还是看不清楚，思维有有点僵化。拿到这一题，立马就想求最值，这是最平庸的方法。  
买股票，追求的是利润，只要第二天比前一天价格更高，就是有利润的。只需要简单的减一些就能解决问题。需要在学一遍算法了。  

# 2. Review
[How To Ask Questions The Smart Way](http://www.catb.org/~esr/faqs/smart-questions.html)  
提问之前必须要做好自己的部分，不能遇到一个问题立马就去提问。  
只有思考才有收获，不然很容易面对同样的错误束手无措。    
  
# 3. Tip
List.add()分为有参和无参两种形式:  
无参:从list的尾部进行插入，size+1(size是指当前包含元素个数);  
有参:即List.add(index,e),再位置index插入e，原来index位置上及其后面的值索引加一;  
如果在声明list时，指定了长度，就类似于声明了一个长度可变的数组，只不过是空的。

```  
List<String> list =new ArrayList<>(2);  
//list.add(1,"OK");直接插入会报错，因为此时size=0;只有index<=size时才能插入;  
list.add("OK");  
list.set(1,"NO");//这里也会报错，set只能替换已经有元素的位置，index<size;  
```  

# 4. Share
[如何有效的报告bug](https://www.chiark.greenend.org.uk/~sgtatham/bugs-cn.html)  
在网上搜问题的时候找到的文章，应该看一下。  
