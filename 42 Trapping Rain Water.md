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
