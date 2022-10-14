[Question](https://leetcode.com/problems/contains-duplicate/)

<img src="0217 Contains Duplicate/image-20221013205737743.png">



My Solution:

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> s = new HashSet<>();
        for(int i: nums)
        {
            if(s.contains(i)) return true;
            s.add(i);
        }
        return false;
    }
}
```

