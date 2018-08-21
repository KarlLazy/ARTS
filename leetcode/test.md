##Algorithm
##最近也就做了两个简单题，还有一个需要使用KMP算法，目前还在看
1.给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
示例:
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

GO

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

2.实现函数 ToLowerCase()，该函数接收一个字符串参数 str，并将该字符串中的大写字母转换成小写字母，之后返回新的字符串。
 
示例 1：
输入: "Hello"
输出: "hello"
示例 2：
输入: "here"
输出: "here"
示例 3：
输入: "LOVELY"
输出: "lovely"

GO

import "strings"
func toLowerCase(str string) string {
    return strings.ToLower(str)
}

这个一开始的思路是字符串转换成数组，然后大写变小写，接着进行字符拼接，最后转化为字符串输出。
不过发现write（）不能拼接字符，只能对字符串进行操作。
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


##Review
##作为一个新入职的小菜鸟，最近一直在啃geth和docker的文档，然后去搭建环境。可能经验不够吧，好多东西出现问题后，不知道如何去处理，直接Google效率也很低。
链接就不发了，目前也就是能看懂流程，感悟什么的暂时还是写不出来的。


##Tip
在ubuntu上学习了一段时间，发现-h真的很强大，看到参数之前第一反应是网上插，现在一般是先-h，找到相应的参数，如果不理解再去查。


##Share 
KMP算法 https://blog.csdn.net/v_july_v/article/details/7041827
