# 0056 Merge Intervals

[Question](https://leetcode.com/problems/merge-intervals/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>



My Solution 1:

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        // sort array
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);

        List<int[]> res = new ArrayList<>();

        int start = intervals[0][0];
        int end = intervals[0][1];

        int i = 1;
        while(i < intervals.length){
            int s = intervals[i][0];
            int e = intervals[i][1];


            if(s <= end){
                end = Math.max(end, e);
            }else{
                res.add(new int[]{start, end});
                start = s; 
                end = e;
            }
            i++;
        }
        // add the last element;
        res.add(new int[]{start, end});
        return res.toArray(new int[res.size()][]);
    }
}
```
