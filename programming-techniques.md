# Programming Techniques

## Use a set to track visited elements

Use a Set to keep track of unique elements or identify whether a particular element has been encountered before. 

```java
public static boolean hasCycle(ListNode head) {
    if (head == null || head.next == null) {
        return false;
    }

    final Set<ListNode> seen = new HashSet<>();
    ListNode current = head;

    while (current.next != null) {
        if (seen.contains(current.next)) return true;

        seen.add(current);
        current = current.next;
    }

    return false;
}
```

## Get the `n`th digit from an int

There are two ways. First, convert the number to a `String`. Second, asdfasdf.

* `Convert to a String`
  ```java
    public static int getDigitAtIndex(int number, int index) {
        String numberStr = Integer.toString(number);

        if (index >= 0 && index < numberStr.length()) {
            char digitChar = numberStr.charAt(index);
            return Character.getNumericValue(digitChar);
        } else {
            return -1;
        }
    }
    ```
* `Use modulo`
    ```java
    private static int getDigitAtIndex(int number, int index) {
    if (index < 0) {
        throw new IllegalArgumentException("Index cannot be negative");
    }

    int counter = 0;
    while (number > 0) {
        int digit = number % 10;
        if (counter == index) {
            return digit;
        }
        counter++;
        number /= 10;
    }

    return -1;
    }
    ```

## One-to-one correspondence between elements

A `Map` allows for unique keys but may contain the same value multiple times. To establish a bidirectional relationship where each key corresponds to a single value and the value corresponds to a single key, you can use two separate Maps.

```java
public static boolean isIsomorphic(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }

    Map<Character, Character> sToTMapping = new HashMap<>();
    Map<Character, Character> tToSMapping = new HashMap<>();

    for (int i = 0; i < s.length(); i++) {
        char charS = s.charAt(i);
        char charT = t.charAt(i);

        if (sToTMapping.containsKey(charS) && sToTMapping.get(charS) != charT
                || tToSMapping.containsKey(charT) && tToSMapping.get(charT) != charS) {
            return false;
        }

        sToTMapping.put(charS, charT);
        tToSMapping.put(charT, charS);
    }

    return true;
}
```

## Swap elements in an array

```java
public static void swapArrayElements(int[] arr, int index1, int index2) {
    int temp = arr[index1];
    arr[index1] = arr[index2];
    arr[index2] = temp;
}
```

## Navigate using pointers

Pointers are variables that store memory addresses or indices.

* `Traversal and comparison`: Pointers are often used to traverse data structures such as arrays, linked lists, strings, and trees.
They enable efficient comparison of elements, making it easy to determine relationships, order, or matches between elements.
* `Searching and matching`: Can be used to search for specific elements within a data structure. For example, finding a target value in an array or locating a substring within a string. They can also be employed to check for matches or patterns, such as substring matching, pattern matching, or sequence alignment.

```java
public static boolean isSubsequence(String s, String t) {
    int sPointer = 0;
    int tPointer = 0;

    while (sPointer < s.length() && tPointer < t.length()) {
        if (s.charAt(sPointer) == t.charAt(tPointer)) {
            sPointer++;
        }
        tPointer++;
    }

    return sPointer == s.length();
}
```
