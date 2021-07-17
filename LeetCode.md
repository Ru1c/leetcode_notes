# 1. Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.


For an example, suppose the array is like A = [2, 8, 12, 15], and the target sum is 20. Then it will return indices 1 and 2, as A[1] + A[2] = 20.

1. prepare a null dict
2. use remain=20-first value in array  to check the remaining values
3. fulfill the dict: array values as dict indicators; array indicators as dict values
4. repeat 2&3 for the array values
5. output the two results dict values representing the 2 array's indicators for the two sum

```

class Solution(object):
    def twoSum(self, nums, target):
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

# 7. Reverse Interger
What is the meaning of “int(a[::-1])” in Python?

https://stackoverflow.com/questions/31633635/what-is-the-meaning-of-inta-1-in-python/31633656

Assuming a is a string. The Slice notation in python has the syntax :

list[start:stop:step]

When you do a[ : : -1], it starts from the end towards the first taking each element, so the a is reversed.
This is applicable for lists/tuples as well.

Example below:

a = '1234'

a[::-1]

'4321'

That just gives you back the string. Then you could convert it to int.

```
class Solution(object):
    def reverse(self,x):
        output = int(str(abs(x))[::-1])
        if output < 2**31:
            if x >= 0:
                return output
            else:
                return -output
        else:
            return 0  

```
    
    
