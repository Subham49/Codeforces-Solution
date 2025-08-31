# 🛠️ B. Fix You  
[1463B - Fix You](https://codeforces.com/problemset/problem/1463/B)

---

### 💡 Problem Statement

You are given a conveyor belt represented as a grid of size `n × m`. Each cell in the grid (except the bottom-right cell `(n, m)`) contains a direction:

- `'R'` → right  
- `'D'` → down  
- The bottom-right cell `(n, m)` contains `'C'` and represents the **counter** where all luggage must end up.

**Rules:**
- A luggage placed at a cell will follow the direction of that cell.
- If it moves off the grid, it is considered **lost**.
- The conveyor belt is **functional** if **every** luggage placed at **any** cell reaches the counter.

Your goal is to determine the **minimum number of cells** you need to **change** (from `'R'` to `'D'` or vice versa) so that the conveyor becomes functional.

---

### 📥 Input

- The first line contains an integer `t` — the number of test cases.  
  (1 ≤ t ≤ 10)

- For each test case:
  - The first line contains two integers `n` and `m` (1 ≤ n, m ≤ 100)
  - The next `n` lines each contain a string of `m` characters (`R`, `D`, or `C`)


### 📤 Output

- For each test case, print the minimum number of cells that must be changed.

---

### 🧪 Examples

#### Input:
4  
3 3  
RRD  
DDR  
RRC  
1 4  
DDDC  
6 9  
RDDDDDRRR  
RRDDRRDDD  
RRDRDRRDR  
DDDDRDDRR  
DRRDRDDDR  
DDRDRRDDC  
1 1  
C

#### Output:
1  
3  
9  
0

---

### 🧠 Logic

To make the conveyor functional:
- All cells in the **last row** (except the bottom-right corner) **must be `R`**, so luggage moves right to reach the counter.
- All cells in the **last column** (except the bottom-right corner) **must be `D`**, so luggage moves down to reach the counter.

So, we just need to:
1. Count how many **`D`** exist in the **last row** → they must be changed to `R`
2. Count how many **`R`** exist in the **last column** → they must be changed to `D`

The sum of these is the **minimum number of changes** required.

---

### ✅ Java Solution

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int testCase = sc.nextInt();

        while (testCase-- > 0) {
            int r = sc.nextInt();
            int c = sc.nextInt();
            String[] mat = new String[r];

            // Read the matrix
            for (int i = 0; i < r; i++) {
                mat[i] = sc.next();
            }

            int ans = 0;

            // Check last column for incorrect 'R's
            for (int i = 0; i < r; i++) {
                if (mat[i].charAt(c - 1) == 'R') {
                    ans++;
                }
            }

            // Check last row for incorrect 'D's
            for (int i = 0; i < c; i++) {
                if (mat[r - 1].charAt(i) == 'D') {
                    ans++;
                }
            }

            System.out.println(ans);
        }

        sc.close();
    }
}
