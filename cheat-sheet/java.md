# Java

## String

```java
StringBuilder s = new StringBuilder();
s.append(String/int/double);
String res = s.toString();

String a, b;
a.equals(b);

// array to String
String[] a = {"a","b","c"};
String b = a.join("", a);

// 
String a = "abdcde";
char b = a.charAt(1);
int c = a.lastIndexOf('d');
```



## Array

```java
// Initial Array
int[] a = new int[4];
int[] a = {1,2,3,4};
int[][] a = {{1,2},{3,4};
int[] a = new int[]{hashmap.keySet()};
```



## Queue

```java
Queue<Integer> q = new ArrayList<>();
Queue<Integer> q = new LinkedList<>();

q.isEmpty(); // return true or false
q.size();
q.offer(); // add element
q.offer(new int[]{1,2});
q.poll(); // remove element
q.peek();  // check element but not remove 
```

## LinkedList

```java
List<Integer> a = new ArrayList<>();
List<Integer> a = new LinkedList<>();
List<Intger> b = new ArrayList<>(a);

int a = b.size(); // get size of list
```
