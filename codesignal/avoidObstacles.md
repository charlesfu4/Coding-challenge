## Aviod Obstacle

You are given an array of integers representing coordinates of obstacles situated on a straight line.

Assume that you are jumping from the point with coordinate 0 to the right. You are allowed only to make jumps of the same length represented by some integer.

Find the minimal length of the jump enough to avoid all the obstacles.


**My Solution**

My thought was to iterate through every number from 2 to the upper limit 1000(the given promise of the largest entry). If the iterative number is the factor of the entry than we can try the next number.  

```java
public int avoidObstacles(int[] inputArray) {
    int i;
    int count;
    for(i = 2; i<1001; i++){
        count = 0;
        for(int j = 0; j<inputArray.length; j++){
            if(inputArray[j] % i == 0)
                break;
            else{
               count++;
               if(count == inputArray.length){
                   return i;
               }
            }
        }
    }
    return i;
}

```

**Other solution**

Similar thought from other also make use of factor detection. But he made use of accumulation that he can aviod setting the upper bound of the searching range.

```java
int avoidObstacles(int[] inputArray) {

    int jump = 1;
    boolean fail = true;

    while(fail) {
        jump++;
        fail = false;
        for(int i=0; i<inputArray.length; i++)
            if(inputArray[i]%jump==0) {
                fail = true;
                break;
            }
    }

    return jump;
}

```
