## All Longest Strings
Given an array of strings, return another array containing all of its longest strings.
**MY solution**
To dectect the longest strings, I decided to sort the length of each string first to identify the longest string. Afterware, I deducted each length of the string by the longest length. In this way, I can identify the entry of the longest strings in the array. Four for loops create a time complexity around O(4N).
```java
public String[] allLongestStrings(String[] inputArray) {
    int[] lenlist = new int[inputArray.length];
    for(int i = 0; i < inputArray.length; i++){
        lenlist[i] = inputArray[i].length();
    }
    int[] copy = Arrays.copyOf(lenlist, lenlist.length);
    // A sorted array with the length of each string
    Arrays.sort(lenlist);
        
    // minus the longest string length  
    for(int i = 0; i < inputArray.length; i++){
        copy[i] -= lenlist[lenlist.length - 1];
    }
    // probe the elements with Zero and add to an Arraylist
    ArrayList<String> longeststrings = new ArrayList<String>();
    for(int i = 0; i < inputArray.length; i++){
        if(copy[i] == 0)
            longeststrings.add(inputArray[i]);
    }
    // Create new String array for the return
    String[] processedstring = new String[longeststrings.size()];
    for(int i = 0; i < longeststrings.size(); i++)
        processedstring[i] = longeststrings.get(i);
    return processedstring; 
}

```

**Brilliant Solution**
As we can observe, the author implement a incremental check on the length of current visited string and the string previously stored. In this way, if the current string is longer than previous ones, the status can be updated. Also, string with the same length will be appended behind. Too smart, IQ 180!

```java
String[] allLongestStrings(String[] inputArray) {

    String l = ""; //full string with "-" separator

    for( String s: inputArray )
    {
        //length is first index of substring
        //if list has same size strings, add this one
        if( l.indexOf("-") == s.length() ) l += s + "-";
        //reset if list has smaller strings
        else if ( l.indexOf("-") < s.length() ) l = s + "-";
    }

    return l.split( "-" );
}

```
