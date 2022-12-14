# LC WEEKLY 307 :
## Links to the individual problems are included below:



- Sort the People (3 points)   --> https://leetcode.com/problems/sort-the-people/

- Longest Subarray With Maximum Bitwise AND (4 points) --> https://leetcode.com/problems/longest-subarray-with-maximum-bitwise-and/

- Find All Good Indices (5 points)  --> https://leetcode.com/problems/find-all-good-indices/
 
- Number of Good Paths (6 points)  --> https://leetcode.com/problems/number-of-good-paths/




### Problems : 

- Sort the People :
```
code :

class Solution:
    def sortPeople(self, names: List[str], heights: List[int]) -> List[str]:
        d = {}
        for i in range(len(names)):
            d[heights[i]] = names[i]


        heights.sort(reverse=True)
        ans = []

        for i in range(len(heights)):
            ans.append(d[heights[i]])


        return ans 


approach :
   - store the names and heights indexes in a dict
   - sort the heights in desc order 
   - then loop through heights and get value from dict and append to answer


```


- Longest Subarray With Maximum Bitwise AND
```

code :

    def longestSubarray(self, nums: List[int]) -> int:
        max_val = max(nums)
        
        count = 0
        ans = 1
        
        for i in range(len(nums)):
            if nums[i] == max_val:
                count += 1
            else:
                count = 0
                
            ans = max(ans,count)
            
            
        return ans 


approach :
   - the bitwise AND of two different numbers will always be strictly less than the maximum of those two numbers
   - so the longest subarray with max bitwise AND would be the subarray containing only the max numbers


```


- Find All Good Indices 

```
code : 

    def goodIndices(self, nums: List[int], k: int) -> List[int]:
        n = len(nums)

        prefix = [0] * n 
        suffix = [0] * n

        prev1 = nums[0]
        count1 = 0
        for i in range(n):
            prefix[i] = count1
            
            if i != 0 and prev1 >= nums[i]:
                count1 += 1
            else:
                count1 = 1

            prev1 = nums[i]
            

        prev2 = nums[-1]
        count2 = 0
        for j in range(n-1,-1,-1):
            suffix[j] = count2
            
            if j != n-1 and prev2 >= nums[j]:
                count2 += 1
            else:
                count2 = 1

            prev2 = nums[j]
            


        ans = []

        for i in range(len(nums)):
            if suffix[i] >= k and prefix[i] >= k:
                ans.append(i)

        return ans 




approach :
   - create a monatonic prefix and suffix array , check non increasing count of each index 
   - then loop through n again , check for each index if suffix[i] >= k and prefix[i] >= k:
   - At every index we want to know if the number of descending prefix elements >= k and number of ascending suffix elements >= k. So we preprocess this info and use it to find the correct indices.

```




















