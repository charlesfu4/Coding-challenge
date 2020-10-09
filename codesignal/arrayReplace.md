## Array Replace

Given an array of integers, replace all the occurrences of elemToReplace with substitutionElem.


**Solution with Stream**

Stream data type appears after Java 8. The datatype gives convenience to operation to streamable data. The solution provide how to use the map function with lambda expression in Java as well. Nice to know that.

```java
int[] arrayReplace(int[] inputArray, int elemToReplace, int substitutionElem) {
    return Arrays.stream(inputArray)
    .map(o -> o == elemToReplace ? substitutionElem : o)
       .toArray();
}

```
