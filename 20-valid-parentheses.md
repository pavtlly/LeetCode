## 题意
#### 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
---
## 题解
#### 经典括号匹配问题，通过栈的形式去进行处理，左括号压入栈中，遇到右括号根据栈顶符号进行匹配，需要特判下，最后栈是不是空的，可能最后左括号有多。
#### c++代码
```c++
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for (int i = 0; i < s.size(); i++) {
            if (s[i] == '(' || s[i] == '[' || s[i] == '{') st.push(s[i]);
            else if (s[i] == ')' && st.size() && st.top() == '(') st.pop();
            else if (s[i] == ']' && st.size() && st.top() == '[') st.pop();
            else if (s[i] == '}' && st.size() && st.top() == '{') st.pop();
            else {
                return false;
            }
        }
        if (st.size() > 0) return false;
        else return true;
    }
};
```
#### python代码
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for c in s:
            # 如果c是 ({[ 则入栈
            if c in ['(','[','{']:
                stack.append(c)
            # 如果c是 )}] 并且栈不为空 则 判断栈顶是否为与之对应的左括号 是则出栈，不是则返回fasle
            elif c == ')' and stack and stack[-1] == '(':
                stack.pop()
            elif c == ']' and stack and stack[-1] == '[':
                stack.pop()
            elif c == '}' and stack and stack[-1] == '{':
                stack.pop()
            else:
                # 如果c是 )}] 栈为空 那么返回false
                # 如果c是 )}] 栈不为空， 但是 栈顶不是与c对应的左括号 那么返回false
                return False
        # 例如"(){}[" ，如果最后栈不为空，那么就是有多余的左括号了
        return not stack
```