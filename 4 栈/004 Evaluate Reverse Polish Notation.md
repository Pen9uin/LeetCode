## - 150 Evaluate Reverse Polish Notation

### 描述

```
    Evaluate the value of an arithmetic expression in Reverse Polish Notation.
    Valid operators are +, -, *, /. Each operand may be an integer or another expression.
    Some examples:
    ["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
    ["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6
```

### 代码
```C++
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        if (tokens.size() == 1) return stoi(tokens[0]);
        stack<int> st;
        for (int i = 0; i < tokens.size(); ++i) {
            if (tokens[i] != "+" && tokens[i] != "-" && tokens[i] != "*" && tokens[i] != "/") {
                st.push(stoi(tokens[i]));
            } else {
                int num1 = st.top(); st.pop();
                int num2 = st.top(); st.pop();
                if (tokens[i] == "+") st.push(num2 + num1);
                if (tokens[i] == "-") st.push(num2 - num1);
                if (tokens[i] == "*") st.push(num2 * num1);
                if (tokens[i] == "/") st.push(num2 / num1);
            }
        }
        return st.top();
    }
};
```
