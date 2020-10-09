## Variable Name

Correct variable names consist only of English letters, digits and underscores and they can't start with a digit.


**My Solution**
Store two ACSII code library for checking condition of the first digit and the others.

```java
boolean variableName(String name) {
    ArrayList<Character> lib = new ArrayList<Character>();
    ArrayList<Character> lib0 = new ArrayList<Character>();
    lib.add((char)95); 
    lib0.add((char)95); 
    
    for(int i = 48; i< 57; i++){
        lib.add((char)i);
    }
    
    for(int i = 65; i< 90; i++){
        lib.add((char)i);
        lib0.add((char)i);
    }
    for(int i = 97; i< 122; i++){
        lib.add((char)i);
        lib0.add((char)i);
    }
    if(!lib0.contains(name.charAt(0)))
        return false; 
    for(int i = 1; i< name.length(); i++){
        if(!lib.contains(name.charAt(i)))
            return false;
    }
    return true;
}

```


**Better Solution**

Ok, brilliant regex solution, should review and practice it.

```java
boolean variableName(String name) {
    return name.matches("[a-zA-Z_][a-zA-Z0-9_]*");
}

```
