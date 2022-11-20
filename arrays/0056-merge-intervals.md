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





My Solution 2: TreeMap

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        for(int[] i: intervals){
            add(i[0], i[1]);
        }

        int i = 0;
        int res[][] = new int[map.size()][2];
        for(Map.Entry<Integer, Integer> m: map.entrySet()){
            res[i++] = new int[]{m.getKey(), m.getValue()};
        }

        return res;
    }

    // use Map to store 
    TreeMap<Integer, Integer> map = new TreeMap<>();

    private void add(int left, int right){
        if(map.floorKey(right) == null
        || map.get(map.floorKey(right)) < left){
            map.put(left, right);
        }else {
            int start = left, end = right;
            while(true){
                int l = map.floorKey(end);
                int r = map.get(l);
                start = Math.min(l, start);
                end = Math.max(r, end);

                map.remove(l);
                if(map.floorKey(end) == null
                || map.get(map.floorKey(end)) < start){
                    break;
                }
            }

            map.put(start, end);
        }
    }
}
```
