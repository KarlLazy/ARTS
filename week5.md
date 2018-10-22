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
[mybatis](http://www.mybatis.org/mybatis-3/zh/index.html)  
最近在学习springboot+mybatis，最直观的感受就是应用起来简单了许多。  
  
# 3. Tip
@Cacheable：主要针对方法配置，能够根据方法的请求参数对其结果进行缓存。当重复使用相同参数调用方法的时候，方法本身不会被调用执行，即方法本身被略过了，取而代之的是方法的结果直接从缓存中找到并返回了。  
@CachePut：保证方法被调用，又希望结果被缓存。这个注释可以确保方法被执行，同时方法的返回值也被记录到缓存中。  
@CachePut和@Cacheable这两个标签可以结合使用，当需要根据请求改变值的时候，利用@CachePut将值改变并写入到缓存中，而@Cacheable标签除了第一次之外，一直是取的缓存的值。  

