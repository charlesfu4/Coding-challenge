## Find Email Domain

An email address such as "John.Smith@example.com" is made up of a local part ("John.Smith"), an "@" symbol, then a domain part ("example.com").

The domain name part of an email address may only consist of letters, digits, hyphens and dots. The local part, however, also allows a lot of different special characters. Here you can look at several examples of correct and incorrect email addresses.

Given a valid email address, find its domain part.


**My Solution**

I make use of regex, it was a good practice. `[\\w|\\W]` matches either word or non-word. `[^@]` the match should be without '@', and then '*' represents 0 to many. End with `@` to search for specific end of '@'.


```java
String findEmailDomain(String address) {
    return address.replaceAll("[\\w|\\W][^@]*@", "");
}

```


**Others Solution**

The others tend to identify the last index of '@' and make a substring.


```java
String findEmailDomain(String address) {
    return address.substring(address.lastIndexOf("@") + 1);
}

```

