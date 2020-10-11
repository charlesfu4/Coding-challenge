## Array max consecutive sum

Given array of integers, find the maximal possible sum of some of its k consecutive elements.

**My Solution**

I made use of a for loop to go through all the element, and an extra inner for loop to add every element for every stop. The time complexity then will be O(k*n), with k the number of consecutive elements, and n the number of elements in the array. This solution is not wise at all.

```java
int arrayMaxConsecutiveSum(int[] inputArray, int k) {
    int max = Integer.MIN_VALUE;
    for(int i = 0; i<inputArray.length-k+1; i++){
        int sum = 0;
        for(int j = 0; j<k;j++){
            sum += inputArray[i+j];
        }
        if(sum >= max)
            max = sum;
    }
    return max;
}
```


**Better Solution**

The solution found the memory pattern of every consecutive members. Therefore, the for loop in my solution can be actually eradicated. By doing this the time complexity comes down to O(n).

```java
int arrayMaxConsecutiveSum(int[] inputArray, int k) {
    int s = 0, ma;
    for(int i = 0; i < k; i++) s += inputArray[i];
    ma = s;
    for(int i = k; i < inputArray.length; i++) {
        s += inputArray[i] - inputArray[i - k];
        ma = Math.max(ma, s);
    }
    return ma;
}
```
