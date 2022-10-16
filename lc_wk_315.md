# LC WEEKLY 315 :
## Links to the individual problems are included below: - sovled 3/4


# https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/


- Largest Positive Integer That Exists With Its Negative :
```
code :

class Solution:
    def findMaxK(self, nums: List[int]) -> int:
        
        nums  = set(nums)
        
        hashmap = defaultdict(int)
        
        for i in nums:
            val = abs(i)
            hashmap[val] += 1
            
        ans = float('-inf')
        for j in hashmap:
            if hashmap[j] == 2:
                ans = max(j,ans)
                
        if ans == float('-inf'):        
            return -1 
        
        return ans
            

approach :
   - convert array to set 
   - store count of each abs value to dict
   - count == 2 , store max


```


# https://leetcode.com/problems/count-number-of-distinct-integers-after-reverse-operations/


-  Count Number of Distinct Integers After Reverse Operations :
```
code :

class Solution:
    def countDistinctIntegers(self, nums: List[int]) -> int:
        hmap = {}
        for i in nums:
            hmap[i] = 1

        
        for i in nums:
            cur_ele = str(i)[::-1]
            
            new_ele = int(cur_ele)
            if new_ele not in hmap:
                hmap[new_ele] = 1
                
                
                
        return len(hmap)
            

approach :
   - freq map 
   - rev each element and check if its in map else add it 


```



# https://leetcode.com/problems/sum-of-number-and-its-reverse/ 


- Sum of Number and Its Reverse

```
code :

class Solution:
    def sumOfNumberAndReverse(self, num: int) -> bool:
    	
        for n in range(0,num+1):
            strN = str(n)		
            strR = strN[::-1]	
            if int(strN)+int(strR)==num:
                return True
        return False
            

approach :
   -  make sure to check num as well (for case num=0), so we go from 0 to num+1
   -  convert int to string
   -  reverse the digits
   -  make sure to convert the string back to int.


```