# 1. Algorithm

- 134 .  [加油站](https://leetcode-cn.com/problems/gas-station/)

在一条环路上有 N 个加油站，其中第 i 个加油站有汽油 gas[i] 升。  
你有一辆油箱容量无限的的汽车，从第 i 个加油站开往第 i+1 个加油站需要消耗汽油 cost[i] 升。你从其中的一个加油站出发，开始时油箱为空。  
如果你可以绕环路行驶一周，则返回出发时加油站的编号，否则返回 -1。    
  
  
```

class Solution {  
    public int canCompleteCircuit(int[] gas, int[] cost) {  
        // 参数检验  
        if (gas == null || cost == null || gas.length == 0 || gas.length != cost.length) {  
            return -1;  
        }  

        // 记录访问的起始点  
        int start = 0;  
        // 加的气和消耗的气的总差值  
        int total = 0;  
        // 从start位置开始，加的气和消耗的气的总差值  
        int sum = 0;  
        for (int i = 0; i < gas.length; i++) {  
            total += (gas[i] - cost[i]);  
            // 如是油箱没有油了  
            if (sum < 0) {  
                // 重新设置油箱中的油  
                sum = gas[i] - cost[i];  
                // 记录新的起点位置  
                start = i;  
            } else {  
                // 油箱中还有油，更新油箱中的油数  
                sum += (gas[i] - cost[i]);  
            }  
        }  
        return total >= 0 ? start : -1;  
    }  
}  
```
这个是我在网上找的一个方法。  
我自己编写的方法考虑不周到，对gas和cost的总和分别进行了计算，在数组非常大的情况下，这种方法会超出限度。  
网上的方法是直接计算差值，而不计算和值，这样就省时省空间，也能够承受住大数组的碾压。  
核心部分都是对当前油的和与消耗进行比较，这个还是比较容易的，就是看是否能够更简单的处理。   

# 2. Review
[slf4j](https://www.slf4j.org/faq.html)  
想搞明白运行时的日志，找到了这个文档，还是蛮不错的。  
  
# 3. Tip
最近遇到一个坑，项目新增亚马逊的短信模块后，就不能正常启动了。  
找了半天才发现是缺少消息推送模块的认证信息，就是用户目录下的.aws，这里储存的是亚马逊的账户信息  

# 4. Share
