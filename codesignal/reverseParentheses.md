## Reverse In Parentheses

Write a function that reverses characters in (possibly nested) parentheses in the input string.

My first thought was to create stacks for elements within the parentheses. However, it did not work in multiple parentheses situation. I also thought about recursive method to pop out multiple parentheses stacks. The sequence was still wrong with this method. Later on, my mind came to stacking the left parentheses itself and pop out when the iteration walk through the right parentheses. The solution is shown as follow.

```java
public String reverseInParentheses(String inputString) {
    String output;
    Stack<Integer> left = new Stack<Integer>();
    StringBuilder input = new StringBuilder(inputString);
    int idx_left;
    for(int i = 0; i < inputString.length(); i++){
        if(input.charAt(i) == '(')
            left.add(i);
        else if(input.charAt(i) == ')'){
            idx_left = left.pop()+1;
            StringBuilder temp = new StringBuilder(input.substring(idx_left, i));
            input.replace(idx_left , i, temp.reverse().toString()); 
        }
    }
    output = input.toString().replace("(", "");
    output = output.replace(")", "");
    return output;
}
```
Here I make use of StringBuilder datastructure to implement a more convenient reversion. 

A more concise code from others is shown as follow.

```java
String reverseInParentheses(String inputString) {
    StringBuilder str = new StringBuilder(inputString);
    int start, end;
    while(str.indexOf("(") != -1){
        start = str.lastIndexOf("(");
        end = str.indexOf(")", start);
        str.replace(start, end + 1, new StringBuilder(str.substring(start+1, end)).reverse().toString());
    }
    return str.toString();
}
```
Basically, this solution save the index of the parentheses, but wisely use the indexOf function to identify the correct coressponding right parenthesesthe solution is brilliant since it saves memory by skipping creating stack.
