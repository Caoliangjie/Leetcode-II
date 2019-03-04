##
给定一个字符串，逐个翻转字符串中的每个单词。

输入: "the sky is blue"
输出: "blue is sky the"

* 无空格字符构成一个单词。
* 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
* 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
###stack的用法
stack的基本操作有：

1.入栈：如s.push(x);

2.出栈:如 s.pop().注意：出栈操作只是删除栈顶的元素，并不返回该元素。

3.访问栈顶：如s.top();

4.判断栈空：如s.empty().当栈空时返回true。

5.访问栈中的元素个数，如s.size（）;
## 代码
```c
class Solution {
public:
    string reverseWords(string s) {
        stack<string> str;##stack是堆栈
        string s0 = "";
        if (s.empty()){
            #s = "";
            return s;
        }
        
        for(int i=0;i<s.length();i++){
            if(s[i] != 32){
                s0 += s[i];
                continue;
            }
            else if(!s0.empty()){
                str.push(s0);
                s0.clear();
            }
        }
        
        if(!s0.empty()){
            str.push(s0);
            s0.clear();
        }
        
        while(!str.empty()){
            
            s0 += str.top();
            str.pop();
            s0 += " ";
        }
            if(s0.empty())
        {
            s = "";
            return s;
        }
        s0.erase(s0.end()-1);
        s = s0;
        return s;
    }
};
```
