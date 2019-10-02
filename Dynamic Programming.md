Maximum Subarray

![image4](https://github.com/Erunning/algorithm_solutions/blob/master/image/image4.png)

遍历数组，算法复杂度O(n)
以第i个元素为结尾的最大子序和 = max(第i个元素，第i个元素+以第i-1个元素为结尾的最大子序和)
再从中再到真正的最大值
```python3
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans_list = [0]
        for x in nums:
            ans_list.append(max(x,ans_list[-1]+x))
        return max(ans_list[1:])
```
