## Digit Degree 

Define digit degree of some positive integer as the number of times we need to replace this number with the sum of its digits until we get to a one digit number.

Given an integer, find its digit degree.

- For n = 5, the output should be digitDegree(n) = 0;

- For n = 100, the output should be digitDegree(n) = 1. 1 + 0 + 0 = 1.

- For n = 91, the output should be digitDegree(n) = 2. 9 + 1 = 10 -> 1 + 0 = 1.
   


**My Solution**

My solution made use of parseInt to walking through every digit an do the calculation.

```java
int digitDegree(int n) {
    int count = 0;
    for(;n > 9; count++){
        String strn = Integer.toString(n);
        n = 0;
        for(int i = 0; i < strn.length(); i++){
            n+=Integer.parseInt(strn.substring(i,i+1));
        }
    }
    return count;
}
```


**Other's Solution**

The solution used arithmetic only. It devide and take the mod of original number to get the correct form of digit. After the division of 10 if the original number is still not 0 then it means that the original number still have at least 2 digits. A recusive return only when the cased is solved to acceptable form of digit. In the end the return number will be the number of times it solve every stage of digit into correct form. 

```java
int digitDegree(int n) {
        if(n/10==0)
            return 0;
        int num =0;
        while (n!=0){
            num+=n%10;
            n/=10;
        }
        return 1 + digitDegree(num);
    }
```

