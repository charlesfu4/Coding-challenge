## Build Palindrome
Given a string, find the shortest possible string which can be achieved by adding characters to the end of initial string to make it a palindrome.

Example

For `st = "abcdc"`, the output should be
`buildPalindrome(st) = "abcdcba"`.

**My Solution**

My Solution reversed the string first and compare the overlapped parts between two string. The extra part them have to be append to build the Palindrome String.

```java
String buildPalindrome(String st) {
    Stack<Character> charstack = new Stack<Character>();
    String reversed = "";
    for(int i : st.getBytes()){
        charstack.add((char) i);
    }
    while(charstack.size() > 0){
        reversed += charstack.pop();
    }
    // special cases first, already meet the palindrome requirement
    if(reversed.equals(st)) return st;
    // normal cases that need additional characters to meet the palindrome
    int i;
    for( i = reversed.length()-1; i>0; i--){
        if(st.indexOf(reversed.substring(0, i)) != -1){
            break;
        }
    }

    return st + reversed.substring(i);
}

```




**Other's Solution**

This guy makes use of recusive to detect zoom in to a tinier scope of the string with number of operation it takes. In this way, it can decide how many character from the end show be taken to build the Palindrome.

```java
String buildPalindrome(String str) {
    int i = 0;
    while (!isPalindrome(str.substring(i))) i++;

    while (--i >= 0) str += str.charAt(i);

    return str;
}

boolean isPalindrome(String s) {
    if (s.length() < 2) return true;

    if (s.charAt(0) != s.charAt(s.length()-1)) return false;

    return isPalindrome(s.substring(1, s.length() - 1));
}

```
