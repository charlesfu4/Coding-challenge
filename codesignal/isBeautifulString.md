## Is Beautiful String

A string is said to be beautiful if each letter in the string appears at most as many times as the previous letter in the alphabet within the string; ie: b occurs no more times than a; c occurs no more times than b; etc.




**My Solution**

My solution was not working for one of the case "aaa" before I add `if(arr[0] == arr[arr.length-1]) return true;`. Otherwise, this solution has a time complexity at O(N^2) which is quite slow.

```java
boolean isBeautifulString(String inputString) {
    int arr[] = new int[inputString.length()];
    
    // change into int
    for(int i = 0; i<inputString.length();i++){
        arr[i] = inputString.charAt(i);
    }
    // sort the array and create array list
    Arrays.sort(arr);
    ArrayList<Integer> arrlst = new ArrayList<Integer>();
    for(int i = 0; i< arr.length; i++){
        arrlst.add(arr[i]);
    }
    
    //check if the first one is 'a'
    if(arr[0] != 97) return false;
    //if there are only 'a' 
    if(arr[0] == arr[arr.length-1]) return true;
    
    // The difference between the max and min
    int diff_minmax = arr[arr.length-1] - arr[0];
    for(int i = 98; i<96+diff_minmax; i++){
        // Means there is a hop
        if(arrlst.indexOf(i) == -1) return false;
        
        // check neighbor elements counts
        if(arrlst.indexOf(i+1)+arrlst.indexOf(i-1)>2*arrlst.indexOf(i))
            return false;
    }
    // The last char check
    if(arr.length + arrlst.indexOf(96+diff_minmax) > 2*arrlst.indexOf(arr[arr.length-1])) 
        return false;
        
    return true;
    
    
}
```

**Brilliant Solution**

This solution is a well structured version of my solution, she made use of a temperary array to count the number of appearances of each alphbet, the time complexity is only O(N). Other people also mentioned using hash map. The time complexity will be also O(N) however, the memory requirement will be larger. 

```java
boolean isBeautifulString(String s) {
    int [] c = new int[26];
    
    for (int i : s.getBytes()) c[i-'a'] ++;
    
    for (int i = 1; i < 26; i ++)
        if (c[i] > c[i-1]) return false;
    
    return true;
}

```
