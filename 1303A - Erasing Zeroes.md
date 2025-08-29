# 🧮 A. Erasing Zeroes
[1303A - Erasing Zeroes](https://codeforces.com/problemset/problem/1303/A)
### 💡 Problem Statement

You are given a binary string `s` consisting of characters `'0'` and `'1'`.

Your goal is to **make all the `1`s form a contiguous subsegment**.  
That is, there should be **no `0`s between the first `1` and the last `1`** in the string.

To achieve this, you may **erase any number of `0`s** (possibly none).  
You need to determine the **minimum number of `0`s to erase**.

---

### 📥 Input

- The first line contains a single integer `t` — the number of test cases.  
  (1 ≤ `t` ≤ 100)

- The next `t` lines contain one string `s` each.  
  Each string has length between 1 and 100.  
  Each character is either `'0'` or `'1'`.

---

### 📤 Output

For each test case, print one integer — the **minimum number of `0`s to erase** to make all `1`s in the string contiguous.

---

### 🧪 Examples

#### Input:
3
010011
0
1111000

shell
Copy code

#### Output:
2
0
0

arduino
Copy code

#### Explanation:

- **Test case 1**: `010011` → Delete two middle `0`s → `0111`
- **Test case 2**: `0` → No `1`s, so already valid → `0` deletions
- **Test case 3**: `1111000` → `1`s already contiguous → `0` deletions

---

### 🧠 Logic

To find the number of `0`s between the **first `1`** and the **last `1`**, follow these steps:
1. Skip all leading `0`s until the first `'1'`.
2. Skip all trailing `0`s after the last `'1'`.
3. Count the `0`s between these two positions.

---

### ✅ Java Solution

```java
import java.util.Scanner;

public class Main {
    public static final void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int testCase = sc.nextInt();

        while(testCase-- > 0) {
            String str = sc.next();
            int zeroCount = 0;
            int i = 0;

            // Skip leading zeros
            while(i < str.length() && str.charAt(i) == '0') {
                i++;
            }

            int j = str.length() - 1;

            // Skip trailing zeros
            while(j >= 0 && str.charAt(j) == '0') {
                j--;
            }

            // Count zeros between first and last '1'
            while(i <= j) {
                if(str.charAt(i) == '0') {
                    zeroCount++;
                }
                i++;
            }

            System.out.println(zeroCount);
        }

        sc.close();
    }
}
