# 📞 Boring Apartments (Codeforces 1433A)

[Codeforces 1433A - Boring Apartments](https://codeforces.com/problemset/problem/1433/A)

In a building with 10,000 apartments, a troublemaker begins calling all **boring apartments** — those whose number consists of the **same digit** repeated — until someone finally answers.

You must calculate how many **keypresses** he made before someone picked up.

---

## 📋 Problem Description

A **boring apartment** is defined as one where all digits are the same, such as `2`, `33`, `444`, `9999`.

He calls them in the following order:
- First all apartments using digit `1`: `1`, `11`, `111`, `1111`
- Then digit `2`: `2`, `22`, `222`, `2222`
- ...
- Until the specified apartment number `x` (which is boring) answers.

Each digit pressed during calling counts as a **keypress**.

---

## 🔢 Input

- First line: one integer `t` (1 ≤ t ≤ 36) — number of test cases.
- Next `t` lines: each line contains a single integer `x` (1 ≤ x ≤ 9999), guaranteed to be a boring number.


## 🖨 Output

- For each test case, print the total number of **digits pressed** before reaching apartment `x`.

---

## ✅ Examples

### Input
4
22
9999
1
777

### Output
13
90
1
66

---
## 🔍 Explanation:
i goes from 1 to 36 to cover all 1 to 4-digit boring numbers (for digits 1 to 9).

temp constructs numbers like: 1, 11, 111, 1111, 2, 22, etc.

sumOfDigits tracks the total digits pressed up to each number.

The precomputed results are stored in a HashMap for fast lookup during test cases.

## 🚀 Sample Code Java

```java
import java.util.*;

public class BoringApartmentsMap {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int testCase = sc.nextInt();

        int temp = 0;
        int sumOfDigits = 0;
        HashMap<Integer, Integer> appVsCountMap = new HashMap<>();

        for (int i = 1; i <= 36; i++) {
            temp = temp * 10 + (int)Math.ceil(i / 4.0);
            sumOfDigits += String.valueOf(temp).length();
            appVsCountMap.put(temp, sumOfDigits);
            if (temp % 1111 == 0) {
                temp = 0;
            }
        }

        while (testCase-- > 0) {
            int appartment = sc.nextInt();
            System.out.println(appVsCountMap.get(appartment));
        }

        sc.close();
    }
}
