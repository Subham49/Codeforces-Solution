# 💡 k-String

[219A - k-String](https://codeforces.com/problemset/problem/219/A)

## 📝 Problem Description

A string is called a **k-string** if it can be represented as **k concatenated copies** of some string.

For example:
- `"aabaabaabaab"` is a 1-string, 2-string, and 4-string.
- It is **not** a 3-string, 5-string, or 6-string.

You are given a string `s`, consisting of lowercase English letters, and a positive integer `k`.

🔧 Your task is to **reorder** the letters in the string `s` in such a way that the resulting string is a **k-string**.

If it’s not possible, print `-1`.

---

## 📥 Input

- The first input line contains an integer `k` (1 ≤ k ≤ 1000).
- The second line contains string `s` (1 ≤ |s| ≤ 1000) consisting of lowercase English letters.


## 📤 Output

- Rearranged string that forms a valid **k-string**, or `-1` if it's not possible.
- If multiple answers exist, print any.

---

## 🧪 Examples

### Example 1

**Input**  
2  
aazz  


**Output**  
azaz

### Example 2

**Input**  
3  
abcabcabz  

**Output**
-1

---

## 🚀 Approach

To form a valid **k-string**, each character must appear a number of times divisible by `k`.

Steps:
1. Count frequency of each character.
2. Check if each frequency is divisible by `k`.
   - If not, print `-1`.
3. Build a base string by taking `(frequency / k)` copies of each character.
4. Concatenate this base string `k` times.


## 💻 Java Solution

```java
import java.util.*;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int k = scanner.nextInt();
        String str = scanner.next();
        int count[] = new int[26];

        // Count frequency of each character
        for (int i = 0; i < str.length(); i++) {
            count[str.charAt(i) - 'a']++;
        }
        
        StringBuilder sb = new StringBuilder();
        int i;

        // Check divisibility and build base string
        for (i = 0; i < 26; i++) {
            if (count[i] % k != 0) break;
            for (int j = 0; j < count[i] / k; ++j) {
                sb.append((char) ('a' + i));
            }
        }

        // Output result
        if (i == 26) {
            for (int j = 0; j < k; ++j) {
                System.out.print(sb);
            }
        } else {
            System.out.println("-1");
        }

        scanner.close();
    }
}
