The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)  

P   A   H   N  
A P L S I I G  
Y   I   R  
And then read line by line: "PAHNAPLSIIGYIR"  

Write the code that will take a string and make this conversion given a number of rows:  

string convert(string s, int numRows);  
  

Example 1:  

Input: s = "PAYPALISHIRING", numRows = 3  
Output: "PAHNAPLSIIGYIR"  

Example 2:  
Input: s = "PAYPALISHIRING", numRows = 4  
Output: "PINALSIGYAHRPI"  
Explanation:  
P     I    N  
A   L S  I G  
Y A   H R  
P     I  

**zigzag 是按照Z字型排列。所以可以设置一个变量来代表方向，正的就是往下走，负的就是往上走**  
**join() make all the items in a tuple into a string**  
```
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if numRows <= 1:
            return s
        
        zigzag = ['' for i in range(numRows)]
        row = 0
        step = 1
        for w in s:
            if row == 0:
                step = 1
            if row == numRows - 1:
                step = -1
            zigzag[row] += w
            row += step
        
        return ''.join((zigzag))
```
