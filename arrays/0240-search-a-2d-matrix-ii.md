# 0240 Search a 2D Matrix II

[Question](https://leetcode.com/problems/search-a-2d-matrix-ii/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



My Solution 1: Intuition

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;

        if(target > matrix[m-1][n-1]
        || target < matrix[0][0]){
            return false;
        }

        for(int[]r: matrix){
            if(r[0] <= target && r[n-1] >= target){
                if(searchArray(r, target)){
                    return true;
                }
            }
        }   
        
        return false;
    }


    private boolean searchArray(int[] row, int target){
        int end = row.length-1;
        int begin = 0;
        while(begin <= end){
            int mid = begin + (end - begin) / 2;
            if(row[mid] == target){
                return true;
            }else if(row[mid] > target){
                end = mid-1;
            }else if(row[mid] < target){
                begin = mid+1;
            }
        }

        return false;
    }
}
```