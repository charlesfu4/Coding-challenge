## Add border

Given a rectangular matrix of characters, add a border of asterisks(*) to it.

```java
picture = ["abc",
           "ded"]
//     |
//     |
//     |
//     |
//     V

addBorder(picture) = ["*****",
                      "*abc*",
                      "*ded*",
                      "*****"]
```
**My solution**
The solution is quite falling apart. I try to iterate through elements and construct the border. It leads to ugly code but it still passed the test cases.

```java
public String[] addBorder(String[] picture) {
    int w = picture.length + 2;
    int l = picture[0].length() + 2;
    int k = l;
    String border = "";
    while(k > 0){
        k--;
        border += '*';
    }
    String[] output = new String[w];
    for(int i = 0; i < w; i++){
        if(i == 0 || i == w - 1){
            output[i] = border;
        }
        else{
            String mixed = "";
            for(int j = 0; j< 3;j++){
                if(j == 0 || j== 2){
                   mixed += '*';
                }
                else
                mixed += picture[i - 1];
            }
            output[i] = mixed;
        }
    }
    return output;
}

```

**Brilliant solution**
This solution shows the fully familiarity of java array. Besides it makes use of replaceAll with regex. I almost forget all the regex. Where '.' represents one instance of any character.

```java
String[] addBorder(String[] picture) {
    String[] framedPicture = new String[picture.length + 2];

    for(int i = 0 ; i < picture.length ; i++) {
        framedPicture[i+1] = '*' + picture[i] + '*';
    }

    framedPicture[0] = framedPicture[picture.length + 1] = framedPicture[1].replaceAll(".","*");

    return framedPicture;
}

```
