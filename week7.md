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
[slf4j](https://www.slf4j.org/faq.html)  
想搞明白运行时的日志，找到了这个文档，还是蛮不错的。  
  
# 3. Tip
最近遇到一个坑，项目新增亚马逊的短信模块后，就不能正常启动了。  
找了半天才发现是缺少消息推送模块的认证信息，就是用户目录下的.aws，这里储存的是亚马逊的账户信息  

# 4. Share
《图利的猫》  
这本书主要关于哲学思考，在这本书里看到了几个不错的例子，对开拓脑洞有帮助。  
