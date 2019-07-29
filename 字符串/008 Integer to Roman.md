## - Integer to Roman

### 描述

```
Given an integer, convert it to a roman numeral.
Input is guaranteed to be within the range from 1 to 3999.
```

### 分析
建立一个数表，每次通过查表找出当前最大的数，减去再继续查表。

### 代码

```
class Solution {
public:
    string intToRoman(int num) {
        const int radix[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        const string symbol[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};

        string roman;
        for (size_t i = 0; num > 0; ++i) {
            int count = num / radix[i];
            num %= radix[i];
            for (; count > 0; --count) roman += symbol[i];
        }
        return roman;
    }
};
```
