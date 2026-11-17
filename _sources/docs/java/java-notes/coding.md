# Interview Coding Questions

## String 

### 1.Count Words in a String
```java
public class CountWords {

    public static void main(String[] args) {
        String str="Pushpa is a good girl";
        int count = str.split(" ").length;
        System.out.println(count);
    }
}
```
```bash
5
```

### 2. Find Most Frequent Character
```java
public class MostFrequentChar {
    public static void main(String[] args) {
        String str="lathathatter";
        str.chars()
                .mapToObj(c->(char)c)
                .collect(Collectors.groupingBy(Function.identity(),Collectors.counting()))
                .entrySet()
                .stream()
                .max(Map.Entry.comparingByValue())
                .ifPresent(System.out::println);
    }
}
```
```bash
t=4
```
### 3. Count Vowels and Consonants
```java
public class ConsonantsAndVowels {
    public static void main(String[] args) {
        String str="javaWorld";;
        int vowels=0;
        int consonants=0;
        for(char ch:str.toCharArray()) {
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' || ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U') {
                vowels++;
            } else {
                consonants++;
            }
        }
        System.out.println("Vowels: " + vowels + " Consonants: " + consonants);
    }
}
```
```bash
Vowels: 3 Consonants: 6
```

### 4. Count Character Frequency
```java
public class CharFrequency {
    public static void main(String[] args) {
        String str="banana";;
        Map<Character,Long> result=str.chars()
                .mapToObj(c->(char) c)
                .collect(Collectors.groupingBy(Function.identity(),LinkedHashMap::new,Collectors.counting()));
        System.out.println(result);
    }
}
```
```bash
{b=1, a=3, n=2}
```

### 5. Check if String Contains Only Digits
```java
public class StringContainsOnlyDigits {
    public static void main(String[] args) {
        String str="2347678";
        boolean onlyDigits=str.chars()
                .allMatch(Character::isDigit);
        if(onlyDigits){
            System.out.println("String contains only digits");
        }else{
            System.out.println("String contains non-digit characters");
        }
    }
}
```
```bash
String contains only digits
```

### 6. Reverse Each Word
```java
public class ReverseEachWord {
    public static void main(String[] args) {
        String str="java code";
        String[] strArr=str.split(" ");;
        for(String s:strArr){// java    code
            {
                for(int i=s.length()-1;i>=0;i--){
                    System.out.print(s.charAt(i));
                }
                System.out.print(" ");
            }
        }
    }
}
```
```bash
avaj edoc    
```

### 7. Find the Longest Word
```java
public class LongestWord {
    public static void main(String[] args) {
        String str="java programming language";;
        String[] strArr=str.split(" ");;
        String result=Arrays.stream(strArr)
                .reduce((a,b)->a.length()>b.length()?a:b)
                .orElse("No words found");
        System.out.println(result);
    }
}
```

### 8. Check Anagram Strings
```java
public class AnagramStrings {
    public static void main(String[] args) {
        String str="earth";;
        String str1="heart";
        
        char[] ch1=str.toCharArray();
        char[] ch2=str1.toCharArray();

        Arrays.sort(ch1);
        Arrays.sort(ch2);

        if(Arrays.equals(ch1,ch2)){
            System.out.println("Anagram");
        }else{
            System.out.println("Not Anagram");
        }
    }
}
```
```bash
Anagram
```

### 9. Remove Duplicate Characters
```java
public class RemoveDuplicateChar {
    public static void main(String[] args) {
        String str="banana";
       str.chars()
               .mapToObj(c->(char)c)
               .distinct()
               .forEach(c-> System.out.print(c));;
    }
}
```
```bash
ban
```

### 10.