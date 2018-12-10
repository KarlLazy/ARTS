# 1. Algorithm

- 189 .  [旋转数组](https://leetcode-cn.com/problems/rotate-array/)

给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。   
    
```

class Solution {
    public void rotate(int[] nums, int k) {
       if(nums == null);
        else{
            k %= nums.length;
            reverse(nums,0,nums.length-1);
            reverse(nums,0,k-1);
            reverse(nums,k,nums.length-1);
        }
    } 
    public void reverse(int []array,int i,int j){
        int temp=0;
        while(i<j){
            temp = array[j];
            array[j] = array[i];
            array[i] =temp;
            i++;
            j--;
        }
    }
}
```
  
算法是通过三个翻转进行的，先对整个数组进行翻转，然后把数组从k处分为两端，分别进行翻转.  
  
```

class Solution {
	public void rotate(int[] nums, int k) {
//       方法1，原地交换 时间n(o),空间n(1)
		k = k % nums.length;
		int p = 0;
		int start = 0;
		for (int i = 0; i < nums.length; i++) {
			p = (p + k) % nums.length;
			if (p == start) {
				p++;
				start++;
				continue;
			}
			nums[start] = nums[start] ^ nums[p];
			nums[p] = nums[start] ^ nums[p];
			nums[start] = nums[p] ^ nums[start];
		}
	}
}
```
这个是用原地方法解决的，感觉比较好，就摘抄下来了。  
异或^：把数字转为二进制，从高位开始进行比较，相同则为0，不相同则为1。  

# 2. Review

  
# 3. Tip
一直对接口有点疑惑。平时开发的时候总听见完成这个接口，测试那个接口，就是不清楚这里的接口到底指什么。
现在就比较清楚了。  
在java语法上，接口就是interface，是对方法的抽象，它是抽象方法的集合，利用接口可以达到API定义和实现分离的目的。  
而在生活常常提到的接口，实际上是API，Application Programming Interface,应用程序编程接口，是一组程序功能集合，通常用在不同系统之间的数据交换。  

# 4. Share
[单元测试](https://baike.baidu.com/item/%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B/1928697?fr=aladdin)  
刚刚接触单元测试，百度百科的解释还是很适合入门的。    
