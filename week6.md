# 1. Algorithm

- 44 .  [通配符匹配](https://leetcode-cn.com/problems/wildcard-matching/)

给定一个字符串 (s) 和一个字符模式 (p) ，实现一个支持 '?' 和 '*' 的通配符匹配。  
'?' 可以匹配任何单个字符。  
' * ' 可以匹配任意字符串（包括空字符串）。  
两个字符串完全匹配才算匹配成功。  
说明:  
s 可能为空，且只包含从 a-z 的小写字母。  
p 可能为空，且只包含从 a-z 的小写字母，以及字符 ? 和 *。      
  
  
```

class Solution {
    public boolean isMatch(String s, String p) {
        int s_len = s.length(), p_len = p.length();
        int s_index = 0, p_index = 0;
        int s_start = 0, p_start = -1;
        while(s_index < s_len){
            if(p_index < p_len && p.charAt(p_index) == '*'){
                s_start = s_index;
                p_start = ++p_index;
            }else if(p_index < p_len && (p.charAt(p_index) == '?' || p.charAt(p_index) == s.charAt(s_index))){
                s_index++;
                p_index++;
            }else if(p_start > -1){
                s_index = ++s_start;
                p_index = p_start;
            }else{
                return false;
            }
        }
        while(p_index < p_len){
            if(p.charAt(p_index) != '*'){
                return false;
            }
            p_index++;
        }
        return true;
    }
}
```
这题的难点在于 * 号的匹配，因为不清楚它代表了几个字符。  
因此可以用贪心的方法，先尝试匹配0个字符，未成功则匹配1个字符，以此类推。     

# 2. Review
[slf4j](https://www.slf4j.org/faq.html)  
想搞明白运行时的日志，找到了这个文档，还是蛮不错的。  
  
# 3. Tip
最近遇到一个坑，项目新增亚马逊的短信模块后，就不能正常启动了。  
找了半天才发现是缺少消息推送模块的认证信息，就是用户目录下的.aws，这里储存的是亚马逊的账户信息  

# 4. Share
《图利的猫》  
这本书主要关于哲学思考，在这本书里看到了几个不错的例子，对开拓脑洞有帮助。  
