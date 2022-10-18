# 0038 Count and Say

[Question](https://leetcode.com/problems/count-and-say/)

![](<../.gitbook/assets/image (5).png>)



```java
class Solution {
    public String countAndSay(int n) {
        if(n==1){
            return "1";
        }

        String s = "1";
        for(int i =1; i < n; i++){
            s  = helper(s);
        }
        
        return s;
    }
    
    
    private String helper(String s){
        StringBuilder res = new StringBuilder();
        
        char l = s.charAt(0);
        int count = 1;
        for(int i = 1; i < s.length(); i++ ){
            if(l == s.charAt(i)){
                count++;
            }else{
                res.append(count);
                res.append(l);
                l = s.charAt(i);
                count = 1;
            }
        }
        res.append(count);
        res.append(l);
        
        return res.toString();
    }
}
```
