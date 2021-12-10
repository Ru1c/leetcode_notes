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
    
#   9. Palindrome Number
The 1st idea that comes to mind is to convert the number into string, and check if the string is a palindrome, but this would require extra non-constant space for creating the string which is not allowed by the problem description.

```

class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """

        return str(x) == str(x)[::-1]
        
```

The 2nd idea would be reverting the number itself, and then compare the number with original number, if they are the same, then the number is a palindrome. 

```

class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        num=0
        if x>0 and x<= 2^31-1:
            a=x
            while (a!=0) :
                rev=a%10
                num=num*10+rev
                a=int(a/10)
            if num==x:
                return 'true'
            else:
                return 'false'
        elif x==0 :
            return 'true'
        else:
            return 'false'
            
```



# 13. Roman to Integer

https://blog.csdn.net/coder_orz/article/details/51448537


```

class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        digits = {"I":1, "V":5, "X":10, "L":50, "C":100, "D":500, "M":1000}
        sum = digits[s[len(s)-1]]
        for i in range(len(s)-1, 0, -1):
            cur = digits[s[i]]
            pre = digits[s[i-1]]
            sum += pre if pre >= cur else -pre
        return sum     

```


# 14. Longest Common Prefix

https://www.youtube.com/watch?v=cGQez9SiScw

https://blog.csdn.net/fuxuemingzhu/article/details/77561186


The 1st idea:  

1_  use TRY-Except to judge if all the strings got same alphabet in the same string position.     

2_  got same (len(sets) = 1), then output the alphabet in a null string.     

3_  not (len(sets) > 1), then break the loop.    

4_  the result un-null string.


```
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        result=""
        i=0
        
        while True:
            try:
                sets= set(string[i] for string in strs)
                print('sets', sets).  # check the distinct different alphabet
                if len(sets) == 1:
                    result += sets.pop()
                    i += 1
                else:
                    break
            except Exception as e:
                break
        
        return result
```

pop() 
* The pop() method removes an arbitrary element from the set and returns the element removed.
* The pop() method returns an arbitrary (random) element from the set. Also, the set is updated and will not contain the element (which is returned).

* If the set is empty, TypeError exception is raised.





# 20. Valid Parentheses


```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack =[]
        lookup = {"(": ")", "{": "}", "[": "]"}
        for parenthese in s :
            if parenthese in lookup:
                stack.append(parenthese)
            elif len(stack) == 0 or lookup[stack.pop()] != parenthese:
                return False
        return len(stack) == 0


```


# 21. Merge Two Sorted Lists

break 7/23



# 35. Search Insert Position 
 
 
 ![image](https://user-images.githubusercontent.com/67846228/135516153-bbe3265e-d4c3-4917-bf95-6406ac4036b5.png) 
 
![image](https://user-images.githubusercontent.com/67846228/135516056-eb1ebbd7-5de5-4e8f-8e88-3ab9fa487ec5.png)


```


class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if target > nums[(len(nums)-1)]:
            return len(nums)
        for i in range(len(nums)):
            if nums[i]>=target :
                return i

```



# 412. Fizz Buzz
 
 range() and a%b==0

```
class Solution(object):
    def fizzBuzz(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        
        result=[]
        for i in range(1,n+1):
            if i%15 ==0 :
                result.append("FizzBuzz")
            elif i%3 ==0 :
                result.append("Fizz")
            elif i%5 ==0 :
                result.append("Buzz")
            else:
                result.append(str(i))
                
        return result

```



# 413. Arithmetic Slices 
 
if make it a harder follow up question: how about change the continues subarrays to incontinoues subsets?

```
class Solution(object):
    def numberOfArithmeticSlices(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ans=0
        dp=0
        
        for i in range(2, len(nums)):
            if nums[i] - nums[i - 1] == nums[i - 1] - nums[i - 2]:
                dp += 1
                ans += dp
            else:
                dp = 0
                
        return ans
```



# 414. Third Maximum Number 

```
class Solution(object):
    def thirdMax(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = list(set(nums))
        if len(nums) < 3:
            return max(nums)
        else:
            nums.remove(max(nums))
            nums.remove(max(nums))
            return max(nums)
            
```


# 53. Maximum Subarray

write down local and global calculation process with examples.

```
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if max(nums)<0:
            return max(nums)
        
        local_max,global_max = 0 , 0
        for num in nums:
            local_max = max(0, local_max + num)
            global_max = max(global_max, local_max)
            
        return global_max
            
```

# 268. Missing Number
reduce function
https://www.geeksforgeeks.org/reduce-in-python/

sol-1:
```

class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return reduce(lambda x,y: x+y, xrange(len(nums)+1)) - sum(nums)
        
        
```
sol-2:
```
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if(len(nums)==0):
            return 0
        nums.sort()
        for i in range(len(nums)):
            if(i!=nums[i]):
                return i
        return len(nums)
```

sol-3:
```
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        if(len(nums)==0):
            return 0
        nums.sort()
        for i in range(len(nums)):
            if(i!=nums[i]):
                return i
        return len(nums)
```


# 448. Find All Numbers Disappeared in an Array 


I got TLE(time limit exceeded) at the first try
```
class Solution(object):
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        re = []
        n = len(nums) 
        lst = list(range(1,n+1))
        for i in range(n):
            if lst[i] not in nums:
                re.append(lst[i])
        return re
            
```
