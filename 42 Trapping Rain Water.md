Example 1:  
Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]  
Output: 6  
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.  
  
Example 2:  
Input: height = [4,2,0,3,2,5]  
Output: 9  

**关键点在于知道如何得出该列的水的体积：每一列的水的体积需要比对左边最高点和右边最高点，选取值更小的最高点 - 该列的高度 便是该列水的体积。**  
使用**双指针**来表示左边最高高度和右边最高高度，需要遍历两次来储存左边最高高度和右边最高高度。 再一次遍历整个高度来计算体积。  
**min(leftheight[i], rightheight[i]) - height[i]**  


```
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        leftheight, rightheight = [0] * len(height), [0] * len(height)

        leftheight[0] = height[0]
        for i in range(1, len(height)):
            leftheight[i] = max(leftheight[i - 1], height[i])
        rightheight[-1] = height[-1]
        for i in range(len(height) - 2, -1, -1):
            rightheight[i] = max(rightheight[i + 1], height[i])

        result = 0
        for i in range(0, len(height)):
            summ = min(leftheight[i], rightheight[i]) - height[i]
            result += summ
        return result
```


