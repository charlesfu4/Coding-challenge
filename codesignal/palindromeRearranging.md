## Palindrome Rearranging

Given a string, find out if its characters can be rearranged to form a palindrome.

Example

For inputString = "aabb", the output should be
palindromeRearranging(inputString) = true.

We can rearrange "aabb" to make "abba", which is a palindrome.


**My Solution**

My thought is to merge and delete same elements that occurs twice in the array. In this way there are two situation where the array has odd length, and even length. In even length, every element should disappear after the iteration. However, in odd length, there can be one element remain in the temp.

```java
public boolean palindromeRearranging(String inputString) {
    ArrayList<Character> temp = new ArrayList<Character>();
    for(int i = 0; i < inputString.length(); i++){
       if(!temp.contains(inputString.charAt(i)))
           temp.add(inputString.charAt(i));
        else{
            System.out.println(inputString.charAt(i));
            temp.remove(temp.indexOf(inputString.charAt(i)));
        }
    }

    if(temp.isEmpty())
       return true;
    if(temp.size() == 1){
        if(inputString.length()%2 == 1)
          return true;
        else
          return false;
    }
    return false;
}

```

**Brilliant Solution**

The solution makes use of signed bit wise left shift on a single 1. So, if there are two occurances of the same character the XOR operants will put the 1 on that bit back to 0. Therefore, the final result 0 is to be expected. However, odd length also need to be considered. We see she made use of the characteristic of ADN operants between two opposite numbers in 2's complement signed number. Where -map = ~(map) + 1. It will only be map when there is a single 1 in the 32-bit integer. Too smart. I need to learn more Jserv course! 

```java
boolean palindromeRearranging(String inputString) {
    int map = 0;
    for(int i=0; i<inputString.length(); i++) {
        map ^= 1 << (inputString.charAt(i) - 'a');
    }
    return map == 0 || (map & -map) == map;
}

```
