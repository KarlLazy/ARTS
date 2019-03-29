# 1. Algorithm

- 20 .  [有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

给定一个只包括 '(',')','{','}','[',']' 的字符串，判断字符串是否有效。  
有效字符串需满足：  
1.左括号必须用相同类型的右括号闭合。  
2.左括号必须以正确的顺序闭合。  
注意空字符串可被认为是有效字符串。  
    
```

func isValid(s string) bool {
	if len(s) == 0 {
		return true
	}

	if len(s)%2 == 1 {
		return false
	}

	flag := true
	m := make(map[byte]byte)
	m['('] = ')'
	m['['] = ']'
	m['{'] = '}'
	sli := make([]byte, 0)

	for i, b := range s {
		if i == 0 && (s[i] == ')' || s[i] == ']' || s[i] == '}') {
			flag = false
			break
		}

		if b == '(' || b == '[' || b == '{' {
			sli = append(sli, byte(b))
		} else if b == ')' || b == ']' || b == '}' {
			right := sli[len(sli)-1]
			sli = sli[:len(sli)-1]
			if m[right] != byte(b) {
				flag = false
				break
			}
		}

		if i == len(s)-1 && len(sli) != 0 {
			flag = false
		}
	}
	return flag
}
```
  
如果是左括号，就添加进slice；如果是右括号，就进行匹配并调slice长度
  

# 2. Review

  
# 3. Tip
在使用golang.time包中，AddDate(y, m, d)方法时，发现对月份的处理和想象中的不一样。比如使用AddDate(0,1,0)时，按照自己的想法会得到一个月后的对应日期，但是对于1月31日来说，增加一个月会得到2月31日，而2月没有31日，所以就会转到三月，最终得到3月3日。
这个方法不适合处理年和月，只用来处理日还是蛮好用的。  

# 4. Share  
