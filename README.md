# DSA-Jump-Game-III
Given an array of non-negative integers arr, you are initially positioned at start index of the array. When you are at index i, you can jump to i + arr[i] or i - arr[i], check if you can reach any index with value 0.

Notice that you can not jump outside of the array at any time.
```
Input: arr = [4,2,3,0,3,1,2], start = 5
Output: true
Explanation: 
All possible ways to reach at index 3 with value 0 are: 
index 5 -> index 4 -> index 1 -> index 3 
index 5 -> index 6 -> index 4 -> index 1 -> index 3 
```
```
class Solution:
    def canReach(self, arr: List[int], start: int) -> bool:
        n = len(arr)
        q = [start]

        while q:
            node = q.pop(0)
            # check if reach zero
            if arr[node] == 0:
                return True
            if arr[node] < 0:
                continue

            # check available next steps
            for i in [node + arr[node], node - arr[node]]:
                if 0 <= i < n:
                    q.append(i)

            # mark as visited
            arr[node] = -arr[node]

        return False
```
