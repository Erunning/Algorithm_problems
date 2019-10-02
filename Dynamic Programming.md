Maximum Subarray

![image4](https://github.com/Erunning/algorithm_solutions/blob/master/image/image4.png)

动态规划往往是寻找到前后两个阶段的关系，即转移方程，把复杂问题线性化，动态地解决问题

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
