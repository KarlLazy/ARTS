# 1. Algorithm

- 231 .  2的幂   
  
给定一个整数，编写一个函数来判断它是否是 2 的幂次方。
  
示例 1:  
输入: 1   
输出: true  
解释: 20 = 1  
  
示例 2:  
输入: 16  
输出: true  
解释: 24 = 16
  
示例 3:  
输入: 218  
输出: false

我的想法是设置一个区间，即[2<<i,2<<(i+1)],如果输入的数在这个区间中，就与边界值进行比较。  
  
  
```

class Solution {  
    public boolean isPowerOfTwo(int n) {
        if(n < 1){
            return false;
        }
        else if(n == 1){
            return true;
        }
        else{
            int i = 0;
            int j = 32;
            int a,b;
            while (j-- >0){
                a = 2<<i;
                b = 2<<(i+1);
                if(n >= a && n<= b){
                    if(n == a || n == b){
                        return true;
                    }
                }
                else
                    i++; 
            }
            return false;
        }
    }
}
```

本来以为自己思路挺简单的，不过看到最优解时还是惊到了。这个方法里只用到了逻辑运算，就解决了问题。当转化为二进制，2的幂只有第一位是1，当减去1之后，原为1的位变为0，剩下的全为1，与运算之后得到的结果位0。  


```
class Solution {
    public boolean isPowerOfTwo(int n) {
        return (n > 0) && (n & (n - 1)) == 0;
    }
}
//如果一个数是2的幂，它与它减去1进行与运算得到的结果应该为0。
```


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
原文看不懂，只能先看些别人嚼过的东西。  
[V神论文摘要](https://mp.weixin.qq.com/s/UPZRVPfu2wNFDCQSbk1Lgg)
