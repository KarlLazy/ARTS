# 1. Algorithm
最近也就做了两个简单题，还有一个需要使用KMP算法，目前还在看
- 1 .   两数之和

 给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
 你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
 
 示例:
 给定 nums = [2, 7, 11, 15], target = 9
 因为 nums[0] + nums[1] = 2 + 7 = 9
 所以返回 [0, 1]
```

 func twoSum(nums []int, target int) []int {
     length := len(nums)
     if length < 2{
         return nil
     }
     for i:=0; i < length; i++ {
         for j:=i+1; j< length; j++{
             if nums[i]+nums[j] == target{
                 return []int{i,j}
             }
         }
     }
       return nil
 }
```

- 709 .   转换成小写字符

实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。
 示例 1：
 输入: "Hello"
 输出: "hello"
 示例 2：
 输入: "here"
 输出: "here"
 示例 3：
 输入: "LOVELY"
 输出: "lovely"
```
 import "strings"
 func toLowerCase(str string) string {
     return strings.ToLower(str)
 }
 
 
  //未通过版
 func toLowerCase(str string) string {
     char_array := []byte(str)
     clen := len(char_array)
     sb := bytes.Buffer{}
     for i := 0; i< clen ;i++{
         if char_array[i] >= 97 && char_array[i] <= 122{
             sb.write(char_array[i] - 32)
         }else{
             sb.write(char_array[i])
         }
     }
     str1 := sb.String()
     return str1
 }
    
}
```


# 2. Review
最近一直在啃geth和docker的文档，然后去搭建环境。可能经验不够吧，好多东西出现问题后，不知道如何去处理，直接Google效率也很低。

# 3. Tip

在ubuntu上学习了一段时间，发现-h真的很强大，之前看到参数第一反应是网上查，现在一般是先-h，找到相应的参数，如果不理解再去查。


# 4. Share
 KMP算法 https://blog.csdn.net/v_july_v/article/details/7041827
