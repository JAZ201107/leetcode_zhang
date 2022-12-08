# 0347 Top K Frequent Elements

[Question](https://leetcode.com/problems/top-k-frequent-elements/description/?envType=study-plan\&id=data-structure-ii)

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

My Solution:

<pre class="language-java"><code class="lang-java"><strong>class Solution {
</strong>    public int[] topKFrequent(int[] nums, int k) {
        List&#x3C;Integer>[] bucket = new List[nums.length+1];
        Map&#x3C;Integer, Integer> frequencyMap = new HashMap&#x3C;Integer, Integer>();
        
        // count number
        for(int n: nums){
            frequencyMap.put(n, frequencyMap.getOrDefault(n,0) + 1);
        }
        
        for(int key: frequencyMap.keySet()){
            int frequency = frequencyMap.get(key);
            if(bucket[frequency] == null){
                bucket[frequency] = new ArrayList&#x3C;>();
            }
            bucket[frequency].add(key);
        }
        
        int[] res = new int[k];
        int postion = 0;
        
        // get value from back
        for(int pos = bucket.length -1; pos >= 0 &#x26;&#x26; postion &#x3C; k; pos--){
            if(bucket[pos] != null){
                for(int i: bucket[pos]){
                    res[postion++] = i; 
                }
            }
        }
        
        return res;
    }
}
</code></pre>
