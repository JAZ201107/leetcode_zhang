# 0752 Open the Lock

[Question](https://leetcode.com/problems/open-the-lock/)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



My Solution:

```java
class Solution {
    public int openLock(String[] deadends, String target) {
        if(target.equals("0000")){
            return 0;
        }
        
        
        Queue<Integer> queue = new LinkedList<>();
        queue.add(0);
        boolean[] seen = new boolean[10000];
        for(String s: deadends){
            seen[Integer.parseInt(s)] = true;
        }
        
        int targ = Integer.parseInt(target);
        if(seen[0]){
            return -1;
        }
        
        
        for(int turns = 1; !queue.isEmpty(); turns++){
            int n = queue.size();
            for(int i =0; i < n; i++){
                int curr = queue.poll();
                for(int j = 1; j < 10000; j *= 10){
                    int mask = curr % (j*10) / j;
                    int masked = curr - (mask * j);
                    
                    for(int k = 1; k < 10; k += 8){
                        int next = masked + (mask + k) % 10 * j;
                        if(seen[next]){
                            continue;
                        }
                        
                        if(next == targ){
                            return turns;
                        }
                        seen[next] = true;
                        queue.add(next);
                    }
                }
            }
        }
        
        return -1;
    }
}
```
