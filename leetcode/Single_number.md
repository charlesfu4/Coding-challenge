## Single Number

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

### My Solution:

Arrays.sort() to sort the given integer array and then check the neighbor number pair by pair.

```java
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i = 0; i < nums.length-1; i+=2){
            if(nums[i] != nums[i+1])
                return nums[i];
        }
        return nums[nums.length-1];
    }
}
```

### **Follow up**: Could you implement a solution with a linear runtime complexity and without using extra memory?


