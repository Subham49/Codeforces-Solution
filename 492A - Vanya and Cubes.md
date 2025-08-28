# 🧱 Vanya and Cubes

[Codeforces 492A - Vanya and Cubes](https://codeforces.com/problemset/problem/492/A)

Vanya has some cubes and wants to build the tallest pyramid possible using them. But this isn’t just any pyramid — each level must contain a number of cubes equal to the **sum of all integers from 1 up to the level number**.

---

## 📋 Problem Description

Vanya got **n** cubes and wants to build a pyramid where:
- Level 1 has `1` cube
- Level 2 has `1 + 2 = 3` cubes
- Level 3 has `1 + 2 + 3 = 6` cubes
- Level 4 has `1 + 2 + 3 + 4 = 10` cubes
- ...
- Level `i` has `1 + 2 + ... + i = i*(i+1)/2` cubes

The pyramid stops when he doesn't have enough cubes for the next level.

### 🔢 Input

- A single integer `n` (1 ≤ n ≤ 10⁴) — the total number of cubes Vanya has.

### 🖨 Output

- Print the **maximum possible height** of the pyramid.

---

## ✅ Examples

### Example 1
Input:
1

Output:
1

shell
Copy code

### Example 2
Input:
25

Output:
4

yaml
Copy code

#### Explanation for Example 2:
- Level 1: needs 1 cube → total = 1
- Level 2: needs 3 cubes → total = 1 + 3 = 4
- Level 3: needs 6 cubes → total = 4 + 6 = 10
- Level 4: needs 10 cubes → total = 10 + 10 = 20
- Level 5: needs 15 cubes → 20 + 15 = 35 → exceeds 25 (not possible)

✅ So, the maximum pyramid height is **4**.

---

## 🔍 Approach

To find the maximum height:
1. Loop through levels `i = 1...` and for each level, compute:
   - `level_cubes = i * (i + 1) / 2`
2. Accumulate `total_cubes` used so far.
3. Stop when `total_cubes + level_cubes > n`.

## 🚀 Sample Code Java

```java
import java.util.*;

public class Main {
    public static final void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int noOfCubes = sc.nextInt();
        int usedCubes = 0;
        int level = 1;
        while(true) {
            int cubeNeeded = (level*(level+1))/2;
            if(usedCubes + cubeNeeded > noOfCubes) {
                break;
            }
            usedCubes += cubeNeeded;
            level++;
        }
        System.out.println(level-1);
        sc.close();
    }
}
