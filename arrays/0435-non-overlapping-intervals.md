# 0435 Non-overlapping Intervals

[Question](https://leetcode.com/problems/non-overlapping-intervals/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>



My Solution 1:

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        // sort according to second element
        Arrays.sort(intervals, (a,b) -> a[1] - b[1]);
        int res = 0;

        int preEnd = intervals[0][1];

        for(int i = 1; i < intervals.length; i++){
            if(intervals[i][0] < preEnd){
                res++;
            }else {
                preEnd = intervals[i][1];
            }
        }


        return res;
    }
}
```





My Solution 2:

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        // sort according to second element
        Arrays.sort(intervals, (a,b) -> a[1] - b[1]);
        

        int count = 1;
        int preEnd = intervals[0][1];

        for(int i = 1; i < intervals.length; i++){
            if(preEnd <= intervals[i][0]){
                count++;
                preEnd = intervals[i][1];
            }
            
        }

        return intervals.length - count;
    }
}
```
