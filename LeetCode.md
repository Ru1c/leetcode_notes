# Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

1. prepare a null dict
2. use remain=20-first value in array  to check the remaining values
3. fulfill the dict: array values as dict indicators; array indicators as dict values
4. repeat 2&3 for the array values
5. output the two results dict values representing the 2 array's indicators for the two sum

```

class Solution(object):
    def twoSum(self, nums, target):
            
#       """
#       :type nums: List[int]
#       :type target: int
#       :rtype: List[int]
#       """
        required = {}
        for i in range(len(nums)):
            if target - nums[i] in required:
                return [required[target - nums[i]],i]
            else:
                required[nums[i]]=i
input_list = [2,8,12,15]
ob1 = Solution()
print(ob1.twoSum(input_list, 20))   

```
    
