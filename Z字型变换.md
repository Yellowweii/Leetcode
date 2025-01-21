### 题目描述：
将一个给定字符串 s 根据给定的行数numRows，以从上往下、从左到右进行Z字形排列。<br>
比如输入字符串为"PAYPALISHIRING" 行数为3时，排列如下：<br>

![image](https://github.com/user-attachments/assets/9cbe0b67-c083-4f48-a7a9-e833193193a9)

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："PAHNAPLSIIGYIR"。<br>
请你实现这个将字符串进行指定行数变换的函数：<br>
string convert(string s, int numRows);

示例 1：<br>
输入：s = "PAYPALISHIRING", numRows = 3<br>
输出："PAHNAPLSIIGYIR"

示例 2：<br>
输入：s = "PAYPALISHIRING", numRows = 4<br>
输出："PINALSIGYAHRPI"<br>
解释：<br>

![image](https://github.com/user-attachments/assets/8af91a49-58ba-44dc-8730-b90b5a6b0d78)


示例 3：<br>
输入：s = "A", numRows = 1<br>
输出："A"

提示：<br>
1 <= s.length <= 1000<br>
s 由英文字母（小写和大写）、',' 和 '.' 组成<br>
1 <= numRows <= 1000

### 题解：
```c++
class Solution {
public:
// 2 * (numRows - 1) - 2 * i
    string convert(string s, int numRows) {
        if(numRows == 1) return s;
        int increment = 2 * (numRows - 1);
        string res = "";
        int anotherIncrement = 0;
        for(int row = 0; row < numRows; row++){
            for(int i = row; i < s.size(); i += increment){
                res += s[i];
                if(row != 0 && row != numRows - 1){
                    anotherIncrement = i + increment - 2 * row;
                    if(anotherIncrement < s.size()){
                        res += s[anotherIncrement];
                    }
                }
            }
        }
        return res;
    }
};
```
