# 📘 A. Petr and Book — Codeforces
[139A - Petr and Book](https://codeforces.com/problemset/problem/139/A)
## 💡 Problem Summary

Petr has a new book with `n` pages and a busy weekly schedule. Each day from **Monday to Sunday**, he reads a fixed number of pages (can be 0). He starts reading on **Monday**, reading daily according to his schedule **without skipping days**.

🔹 The goal is to determine on **which day of the week** he will read the **last page** of the book.

---

## 📥 Input

- First line: integer `n` (1 ≤ n ≤ 1000) — number of pages in the book.
- Second line: 7 space-separated integers — pages Petr can read on each day of the week starting from **Monday** to **Sunday**.

It is guaranteed that the sum of the weekly reading schedule is at least 1 (i.e., he can eventually finish the book).


## 📤 Output

Print a single integer — the **day of the week** (1 to 7) when Petr finishes reading the book.  
Days are numbered as follows:

1 → Monday  
2 → Tuesday  
3 → Wednesday  
4 → Thursday  
5 → Friday  
6 → Saturday  
7 → Sunday  

---

## ✅ Examples

### Example 1

**Input**  
100  
15 20 20 15 10 30 45


**Output**  
6


### Example 2

**Input**  
2  
1 0 0 0 0 0 0


**Output**  
1


---

## 🚀 Strategy

The approach is straightforward:

1. Use a loop to simulate reading days starting from index 0 (Monday).
2. Subtract the pages Petr can read that day from the total pages.
3. Stop when total pages reach 0 or less.
4. Print the current day index + 1 (to match 1-based output).


## 🧠 Java Solution

```java
import java.util.*;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int arr[] = new int[7];

        for (int i = 0; i < arr.length; i++) {
            arr[i] = scanner.nextInt();
        }

        int ind = 0;
        while (true) {
            n -= arr[ind];
            if (n <= 0) {
                System.out.println(ind + 1);
                break;
            }
            ind = (ind + 1) % 7;
        }

        scanner.close();
    }
}
