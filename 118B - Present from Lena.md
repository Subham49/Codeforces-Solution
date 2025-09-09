# 🎁 Present from Lena – Codeforces Problem B

[118B - Present from Lena](https://codeforces.com/problemset/problem/118/B)

## 🧵 Problem Description

Vasya's birthday is approaching and Lena decided to sew a patterned handkerchief for him as a present.

The pattern consists of digits from `0` to `n`, arranged to form a **rhombus**, where:
- The **largest digit `n`** is at the **center**.
- The digits **decrease** as they move toward the **edges**.

Each line is:
- Center-aligned with appropriate spaces,
- Contains digits increasing from 0 to `i`, and then decreasing back to 0,
- Digits are separated by **a single space**, with **no trailing spaces**.

---

## ✅ Input

A single integer `n`  
(2 ≤ n ≤ 9)


## 🎯 Output

Print the **rhombus pattern** using digits from `0` to `n` according to the described format.

---

## 💡 Examples

### Input
2


### Output
```
    0  
  0 1 0  
0 1 2 1 0  
  0 1 0  
    0  
```
### Input
3


### Output
```
      0  
    0 1 0  
  0 1 2 1 0  
0 1 2 3 2 1 0  
  0 1 2 1 0  
   0 1 0  
     0  
```
---

## 🧠 Solution Approach

- First, print the **upper half** of the rhombus (including the middle row).
- Then, print the **lower half** in reverse order.
- For each line:
  - Print leading spaces to center-align the digits.
  - Print digits increasing from `0` to `i`.
  - Then print digits decreasing from `i-1` back to `0`.
  - Add a space between all digits except after the last one.


## 💻 Java Implementation

```java
import java.util.Scanner;

public class PresentFromLena {

    public static final void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        fun(n);
        sc.close();
    }

    public static void fun(int n) {
        for (int i = 0; i <= n; i++) {
            print(i, n);
        }
        for (int i = n - 1; i >= 0; i--) {
            print(i, n);
        }
    }

    public static void print(int i, int n) {
        for (int j = 1; j <= 2 * (n - i); j++) {
            System.out.print(" ");
        }
        for (int j = 0; j <= i; j++) {
            System.out.print(j);
            if (i != 0 || j != 0) System.out.print(" ");
        }
        for (int j = i - 1; j >= 0; j--) {
            System.out.print(j);
            if (j != 0) System.out.print(" ");
        }
        System.out.println();
    }
}
