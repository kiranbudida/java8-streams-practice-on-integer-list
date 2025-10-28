````markdown
# 🧠 Java 8 Streams Practice – 40 Questions with Solutions & Explanations

This repository contains **40 Java 8 Stream API problems** with complete solutions, brief explanations, and sample outputs.  
Each question helps you **progressively master** core to advanced stream operations — perfect for interview prep and daily practice.

---

## ⚙️ Setup

All problems use the same list of integers:

```java
List<Integer> numbers = Arrays.asList(7, 10, 9, 12, 8, 1, 2, 5, 11, 4, 3, 6);
````

---

## 🧩 Section 1: Basic Stream Operations (1–10)

### **1. Print all numbers using Stream**

```java
numbers.stream().forEach(System.out::println);
// forEach() → terminal operation that processes each element
// Output: 7 10 9 12 8 1 2 5 11 4 3 6
```

---

### **2. Print all even numbers**

```java
numbers.stream()
       .filter(n -> n % 2 == 0) // filter() → keeps elements matching the condition
       .forEach(System.out::println);
// Output: 10 12 8 2 4 6
```

---

### **3. Print all odd numbers**

```java
numbers.stream()
       .filter(n -> n % 2 != 0)
       .forEach(System.out::println);
// Output: 7 9 1 5 11 3
```

---

### **4. Find all numbers greater than 5**

```java
numbers.stream()
       .filter(n -> n > 5)
       .forEach(System.out::println);
// Output: 7 10 9 12 8 11 6
```

---

### **5. Square each number**

```java
numbers.stream()
       .map(n -> n * n) // map() → transforms each element
       .forEach(System.out::println);
// Output: 49 100 81 144 64 1 4 25 121 16 9 36
```

---

### **6. Sort numbers in ascending order**

```java
numbers.stream()
       .sorted() // sorted() → sorts elements in natural order
       .forEach(System.out::println);
// Output: 1 2 3 4 5 6 7 8 9 10 11 12
```

---

### **7. Sort numbers in descending order**

```java
numbers.stream()
       .sorted(Comparator.reverseOrder()) // reverse order sorting
       .forEach(System.out::println);
// Output: 12 11 10 9 8 7 6 5 4 3 2 1
```

---

### **8. Count numbers greater than 8**

```java
long count = numbers.stream()
                    .filter(n -> n > 8)
                    .count(); // count() → terminal operation that returns count
System.out.println(count);
// Output: 4
```

---

### **9. Find minimum number**

```java
int min = numbers.stream()
                 .min(Integer::compareTo) // min() → returns smallest element
                 .get();
System.out.println(min);
// Output: 1
```

---

### **10. Find maximum number**

```java
int max = numbers.stream()
                 .max(Integer::compareTo) // max() → returns largest element
                 .get();
System.out.println(max);
// Output: 12
```

---

## 🧠 Section 2: Intermediate Operations (11–20)

### **11. Find sum of all numbers**

```java
int sum = numbers.stream()
                 .reduce(0, Integer::sum);
// reduce() → combines elements into one result (here, summing)
// Output: 78
```

---

### **12. Find average of all numbers**

```java
double avg = numbers.stream()
                    .mapToInt(Integer::intValue)
                    .average() // returns OptionalDouble
                    .orElse(0);
System.out.println(avg);
// Output: 6.5
```

---

### **13. Find 2nd smallest number**

```java
int secondSmallest = numbers.stream()
                            .sorted()
                            .skip(1) // skip the first (smallest)
                            .findFirst()
                            .get();
System.out.println(secondSmallest);
// Output: 2
```

---

### **14. Find 2nd largest number**

```java
int secondLargest = numbers.stream()
                           .sorted(Comparator.reverseOrder())
                           .skip(1)
                           .findFirst()
                           .get();
System.out.println(secondLargest);
// Output: 11
```

---

### **15. Remove duplicates**

```java
numbers.stream()
       .distinct() // distinct() → removes duplicate elements
       .forEach(System.out::println);
// Output: (same list as input since no duplicates)
```

---

### **16. Print first 5 numbers**

```java
numbers.stream()
       .limit(5) // limit() → takes first N elements
       .forEach(System.out::println);
// Output: 7 10 9 12 8
```

---

### **17. Skip first 5 numbers**

```java
numbers.stream()
       .skip(5) // skip() → skips first N elements
       .forEach(System.out::println);
// Output: 1 2 5 11 4 3 6
```

---

### **18. Check if any number greater than 10**

```java
boolean anyMatch = numbers.stream()
                          .anyMatch(n -> n > 10); // returns true/false
System.out.println(anyMatch);
// Output: true
```

---

### **19. Check if all numbers are positive**

```java
boolean allPositive = numbers.stream()
                             .allMatch(n -> n > 0);
System.out.println(allPositive);
// Output: true
```

---

### **20. Find first element**

```java
int first = numbers.stream()
                   .findFirst()
                   .get();
// findFirst() → returns first element of the stream
System.out.println(first);
// Output: 7
```

---

## 🚀 Section 3: Advanced Operations (21–30)

### **21. Find distinct squares**

```java
numbers.stream()
       .map(n -> n * n)
       .distinct()
       .forEach(System.out::println);
// Output: 49 100 81 144 64 1 4 25 121 16 9 36
```

---

### **22. Sort even numbers only**

```java
numbers.stream()
       .filter(n -> n % 2 == 0)
       .sorted()
       .forEach(System.out::println);
// Output: 2 4 6 8 10 12
```

---

### **23. Convert numbers to string list**

```java
List<String> strList = numbers.stream()
                              .map(String::valueOf)
                              .collect(Collectors.toList());
// collect() → terminal operation that gathers elements into a collection
System.out.println(strList);
// Output: [7, 10, 9, 12, 8, 1, 2, 5, 11, 4, 3, 6]
```

---

### **24. Partition numbers into even and odd**

```java
Map<Boolean, List<Integer>> partition = numbers.stream()
        .collect(Collectors.partitioningBy(n -> n % 2 == 0));
// partitioningBy() → splits elements into 2 groups (true/false)
System.out.println(partition);
// Output: {false=[7, 9, 1, 5, 11, 3], true=[10, 12, 8, 2, 4, 6]}
```

---

### **25. Group numbers by remainder when divided by 3**

```java
Map<Integer, List<Integer>> grouped = numbers.stream()
        .collect(Collectors.groupingBy(n -> n % 3));
// groupingBy() → groups elements by a classifier function
System.out.println(grouped);
// Output: {0=[9, 12, 6], 1=[7, 10, 1, 4], 2=[8, 2, 5, 11]}
```

---

### **26. Find product of all numbers**

```java
int product = numbers.stream()
                     .reduce(1, (a, b) -> a * b);
System.out.println(product);
// Output: 479001600
```

---

### **27. Find all numbers ending with digit 1**

```java
numbers.stream()
       .filter(n -> n % 10 == 1)
       .forEach(System.out::println);
// Output: 1 11
```

---

### **28. Find numbers between 3 and 8**

```java
numbers.stream()
       .filter(n -> n > 3 && n < 8)
       .forEach(System.out::println);
// Output: 7 5 4 6
```

---

### **29. Get statistics summary**

```java
IntSummaryStatistics stats = numbers.stream()
                                    .mapToInt(Integer::intValue)
                                    .summaryStatistics();
// summaryStatistics() → gives count, sum, min, avg, max
System.out.println(stats);
// Output: IntSummaryStatistics{count=12, sum=78, min=1, average=6.500000, max=12}
```

---

### **30. Convert to array**

```java
Integer[] arr = numbers.stream().toArray(Integer[]::new);
System.out.println(Arrays.toString(arr));
// Output: [7, 10, 9, 12, 8, 1, 2, 5, 11, 4, 3, 6]
```

---

## 🎯 Section 4: Bonus Challenges (31–40)

### **31. Find top 3 largest numbers**

```java
numbers.stream()
       .sorted(Comparator.reverseOrder())
       .limit(3)
       .forEach(System.out::println);
// Output: 12 11 10
```

---

### **32. Find bottom 3 smallest numbers**

```java
numbers.stream()
       .sorted()
       .limit(3)
       .forEach(System.out::println);
// Output: 1 2 3
```

---

### **33. Multiply each even number by 2**

```java
numbers.stream()
       .filter(n -> n % 2 == 0)
       .map(n -> n * 2)
       .forEach(System.out::println);
// Output: 20 24 16 4 8 12
```

---

### **34. Print numbers along with their squares**

```java
numbers.stream()
       .forEach(n -> System.out.println(n + " → " + (n * n)));
// Output: e.g. 7 → 49, 10 → 100, ...
```

---

### **35. Find sum of squares of even numbers**

```java
int sumSquaresEven = numbers.stream()
                            .filter(n -> n % 2 == 0)
                            .map(n -> n * n)
                            .reduce(0, Integer::sum);
System.out.println(sumSquaresEven);
// Output: 360
```

---

### **36. Find average of odd numbers**

```java
double avgOdd = numbers.stream()
                       .filter(n -> n % 2 != 0)
                       .mapToInt(Integer::intValue)
                       .average()
                       .orElse(0);
System.out.println(avgOdd);
// Output: 6.0
```

---

### **37. Find all numbers starting with digit '1'**

```java
numbers.stream()
       .filter(n -> String.valueOf(n).startsWith("1"))
       .forEach(System.out::println);
// Output: 10 12 11 1
```

---

### **38. Find sum of first 5 even numbers**

```java
int sumEven5 = numbers.stream()
                      .filter(n -> n % 2 == 0)
                      .limit(5)
                      .reduce(0, Integer::sum);
System.out.println(sumEven5);
// Output: 36
```

---

### **39. Sort by square values**

```java
numbers.stream()
       .map(n->n*n)
       .sorted()
       .forEach(System.out::println);
// Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144]
```

---

### **40. Convert to comma-separated string**

```java
String joined = numbers.stream()
                       .map(String::valueOf)
                       .collect(Collectors.joining(", "));
// joining() → concatenates stream elements into a single String
System.out.println(joined);
// Output: 7, 10, 9, 12, 8, 1, 2, 5, 11, 4, 3, 6
```

---

## 🏁 Summary of Concepts Covered

✅ Stream creation
✅ Intermediate operations: `filter`, `map`, `sorted`, `distinct`, `limit`, `skip`
✅ Terminal operations: `forEach`, `count`, `reduce`, `collect`, `findFirst`, `anyMatch`, `allMatch`
✅ Collectors: `groupingBy`, `partitioningBy`, `joining`, `toList`
✅ Numeric Streams: `mapToInt`, `average`, `summaryStatistics`
✅ Advanced use-cases with `Comparator`, `Optional`, and `reduce`

---

> 💡 **Tip:** Run each snippet independently in a `main()` method to observe output and understand how intermediate vs terminal operations behave.
