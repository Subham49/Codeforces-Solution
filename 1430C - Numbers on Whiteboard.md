# 🧮 Numbers on Whiteboard
[1430C - Numbers on Whiteboard](https://codeforces.com/problemset/problem/1430/C)
## 💡 Problem Summary

You are given integers from `1` to `n` written on a whiteboard. In one operation, you can:

- Erase any two numbers `a` and `b`
- Replace them with `ceil((a + b) / 2)`

You are allowed to perform this operation exactly `n − 1` times, after which only one number will remain. Your goal is to **minimize** that final number.

---

## 📥 Input

- First line: single integer `t` — number of test cases (`1 ≤ t ≤ 1000`)
- Each test case contains a single integer `n` (`2 ≤ n ≤ 2×10⁵`)

It is guaranteed that the total sum of all `n` across all test cases does not exceed `2×10⁵`.

## 📤 Output

For each test case:

- First line: the smallest possible number left on the board after `n-1` operations.
- Next `n-1` lines: pairs `a` and `b` representing the numbers removed in each operation.

---

## ✅ Example

**Input**  
1  
4  


**Output**  
2  
4 2  
3 3  
3 1  

---

## 🚀 Strategy

To minimize the remaining number:

- Use a **max-heap** (priority queue) to always combine the two **largest** numbers.
- Insert the ceiling of their average back into the heap.
- Repeat until one number remains.


## 🧠 Java Solution

```java
import java.util.*;

public class NumbersOnWhiteboard {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int testCase = sc.nextInt();

        while (testCase-- > 0) {
            int n = sc.nextInt();
            PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
            List<String> ans = new ArrayList<>();

            // Add all numbers from 1 to n
            for (int i = 1; i <= n; i++) {
                pq.add(i);
            }

            // Combine until one number remains
            while (pq.size() > 1) {
                int a = pq.remove();
                int b = pq.remove();

                int avg = (int) Math.ceil((a + b) / 2.0);
                ans.add(a + " " + b);
                pq.add(avg);
            }

            // Output result
            System.out.println(pq.remove());
            for (String str : ans) {
                System.out.println(str);
            }
        }

        sc.close();
    }
}
