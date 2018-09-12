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
```
class Solution {
    public boolean isPowerOfTwo(int n) {
        return (n > 0) && (n & (n - 1)) == 0;
    }
}
```

# 2. Review
# 3. Tip
# 4. Share
