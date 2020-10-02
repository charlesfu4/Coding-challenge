## IsLucky
Ticket numbers usually consist of an even number of digits. A ticket number is considered lucky if the sum of the first half of the digits is equal to the sum of the second half.

My solution takes two integers for storing sum and compare. Most of the others solution used only a single integer and operates with sum and deduction in two phase. This strategy benefits from less space usage. Meanwhile, I forget Java's character is actually mapping to a 4 bit integer number. Therefore, there is no need to call Character.getNumericValue(c) when doing the summation or deduction operation.

**Brilliant Solution**
```java
boolean isLucky(int n) {

    String s = n+"";
    int sum = 0;

    for(int i=0; i<s.length()/2; i++)
        sum+=(s.charAt(i)-s.charAt(s.length()-1-i));

    return sum==0;
}
```
