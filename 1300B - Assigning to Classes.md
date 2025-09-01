# 🏫 Assigning to Classes  
[1300B - Assigning to Classes](https://codeforces.com/problemset/problem/1300/B)


### 💡 Problem Statement

You are given `2n` students, each with a certain **skill level**. You want to divide them into **two classes**, such that:

- Each class has an **odd number of students**.
- Every student is assigned to exactly one class.
- The **skill level of a class** is defined as the **median** of the skill levels of its students.

Your goal is to find a way to divide the students into two such valid classes such that the **absolute difference between the medians of the two classes is minimized**.

---

### 🧠 What is a Median?

For an odd-length array `[a1, a2, ..., a(2k+1)]`:
- Sort the array → `[b1, b2, ..., b(2k+1)]`
- The **median** is `b(k+1)`

---

### 📥 Input

- First line: integer `t` — number of test cases (1 ≤ `t` ≤ 10⁴)
- For each test case:
  - First line: integer `n` (1 ≤ `n` ≤ 10⁵)
  - Second line: `2n` integers — skill levels of the students  
    (1 ≤ `ai` ≤ 10⁹)

It is guaranteed that the **sum of all `n` values across all test cases does not exceed 10⁵**.


### 📤 Output

For each test case, print a single integer — the **minimum possible absolute difference between the skill levels (medians) of the two classes**.

---

### 🧪 Examples

#### Input
3  
1  
1 1  
3  
6 5 4 1 2 3  
5  
13 4 20 13 2 5 8 3 17 16


#### Output
0  
1  
5  


---

### 🧠 Explanation

To minimize the difference in medians:
1. Sort the list of student skill levels.
2. The **median of one class** will be around the `n`-th smallest value.
3. The **median of the other class** will be around the `(n-1)`-th smallest value.
4. The **minimum possible difference** between medians is then:
arr[n] - arr[n - 1]

### ✅ Java Solution

```java
import java.util.*;

public class Main {
 public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);
     int testCase = sc.nextInt();

     while (testCase-- > 0) {
         int n = sc.nextInt();
         int[] arr = new int[2 * n];

         for (int i = 0; i < 2 * n; i++) {
             arr[i] = sc.nextInt();
         }

         Arrays.sort(arr);

         // Minimum difference between two medians
         System.out.println(arr[n] - arr[n - 1]);
     }

     sc.close();
 }
}
```
### 📊 Time and Space Complexity
Time Complexity: O(t * n log n) — due to sorting each array of 2n elements

Space Complexity: O(n) per test case

