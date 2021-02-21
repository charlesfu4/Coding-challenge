## Reverse String

Write a function that reverses a string. The input string is given as an array of characters `char[]`.

**Do not allocate extra space for another array**, you must do this by modifying the input array in-place with O(1) extra memory.

You may assume all the characters consist of printable ascii characters.

### My Solution

To stick to O(1) memory boundary. I utilize a temporary char to store the targeted char that is going to be changed. And simply excahnging the char pairs(head and tail) one by one until the for loop reaches the middle.

```Java
class Solution {
    public void reverseString(char[] s) {
        char tmp = '\0';
        for(int i = 0; i < s.length/2; i++){
            tmp = s[i];
            s[i] = s[s.length-1-i];
            s[s.length-1-i] = tmp;
        }
    }
}
```

```
Operation faster than 96.34% of Java online submissions for Reverse String.
Memory Usage: 45.8 MB, less than 69.78% of Java online submissions for Reverse String.
```


