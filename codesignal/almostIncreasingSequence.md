## almostincreasingSequence
Given a sequence of integers as an array, determine whether it is possible to obtain a strictly increasing sequence by removing no more than one element from the array.

```java

public boolean almostIncreasingSequence(int[] a) {
    int count1 = 0 , count2 = 0;
    for(int i = 0 ; i < a.length-1 ; i++){
        if(a[i] >= a[i+1]) count1++;
    }

    for(int i = 0 ; i < a.length-2 ; i++){
        if(a[i] >= a[i+2]) count2++;
    }
     return (count1 <=1) && (count2 <= 1);
}

```
To assure strictly ascending, we check both the number on the right and the one on the left.This concept can be transfered into checking thre consecutive numbers at the same time. By giving the limited numbers of counts. We exclude the situation where the double check does not pass. Therefore, the almostincreasing condition will happen when both counts are smaller or equal to 1. 

My first solution for this problem was to use a for loop with ArrayList to remove element one by one. Afterward, we called sort method on the copied Arraylist and check if it is still the same with the previous one. This method failed when the array includes three same elements.
```java
int[] threesame = {1,2,3,5,5,5};
```
My second idea was similar to the solution which works. However, I check only the (i+1) element without checking the (i+2) one. This method also suffers from three duplicate elements.

