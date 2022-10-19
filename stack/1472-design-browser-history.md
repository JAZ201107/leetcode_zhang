# 1472 Design Browser History

[Question](https://leetcode.com/problems/design-browser-history/)

![](<../.gitbook/assets/image (1).png>)



My Solution1: Stack

```java
class BrowserHistory {
    
    Stack<String> BackH;
    Stack<String> ForwH;

    public BrowserHistory(String homepage) {
        BackH = new Stack<>();
        ForwH = new Stack<>();
        
        BackH.push(homepage);
    }
    
    public void visit(String url) {
        BackH.push(url);
        ForwH.clear();
    }
    
    public String back(int steps) {
        while(steps>0 && BackH.size()>1){
            steps--;
            ForwH.push(BackH.pop());
        }
        
        return BackH.peek();
    }
    
    public String forward(int steps) {
        while(steps>0 && !ForwH.isEmpty()){
            steps--;
            BackH.push(ForwH.pop());
        }
        
        return BackH.peek();
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```



My Solution2: Double Linked List

```java
class BrowserHistory {
    
    class Node{
        String url;
        Node pre, next;
        public Node(String url){
            this.url = url;
            pre = null;
            next = null;
        }
    }

    Node head, curr;
    
    public BrowserHistory(String homepage) {
        this.head = new Node(homepage);
        this.curr = head;
    }
    
    public void visit(String url) {
        Node temp = new Node(url);
        curr.next = temp;
        temp.pre = curr;
        curr = temp;
    }
    
    public String back(int steps) {
        while(curr.pre != null && steps > 0){
            steps--;
            curr = curr.pre;
        }
        return curr.url;
    }
    
    public String forward(int steps) {
        while(curr.next != null && steps > 0){
            steps--;
            curr = curr.next;
        }
        
        return curr.url;
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```



