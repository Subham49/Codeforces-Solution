# 🔐 A. Repeating Cipher  
[1095A - Repeating Cipher](https://codeforces.com/problemset/problem/1095/A)

---

### 💡 Problem Statement

Polycarp loves ciphers. He has invented his own cipher called **repeating cipher**.

This cipher works by **repeating each character in the string** a certain number of times based on its position:

- The **1st character** is written **once**  
- The **2nd character** is written **twice**  
- The **3rd character** is written **three times**  
- ...  
- The **m-th character** is written **m times**

For example, for `s = "bab"`, the encryption goes as follows:
- `'b'` → `'b'`  
- `'a'` → `'aa'`  
- `'b'` → `'bbb'`  

So the encrypted string is:
"baabbb"

Given such an encrypted string `t`, your task is to **decrypt** it and retrieve the original string `s`.

---

### 📥 Input

- The first line contains an integer `n` — the length of the encrypted string  
  (`1 ≤ n ≤ 55`)

- The second line contains the encrypted string `t` of length exactly `n`.  
  It contains only lowercase English letters.


### 📤 Output

- Print the original string `s` from which the encrypted string `t` was generated.

---

### 🧪 Examples

#### Input:
6  
baabbb

#### Output:
bab



#### Input:
10  
ooopppssss


#### Output:
oops



#### Input:
1  
z


#### Output:
z



### 🧠 Logic

To decrypt the encrypted string:

1. Start at index `0` of the encrypted string.
2. The first character of `s` appears once, the second character appears twice, the third character three times, and so on.
3. Keep a counter `i` starting from 1 and increment it each time.
4. For each step, pick the current character and move `i` steps forward.
5. Repeat until the end of the string.

---

### ✅ Java Solution

```java
import java.util.Scanner;

public class Main {
    public static final void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int length = sc.nextInt();
        String str = sc.next();
        int ind = 0;
        String ans = "";

        // Start from 1 since the first character is repeated once
        for (int i = 1; ind < length; i++) {
            ans = ans + str.charAt(ind);
            ind += i;
        }

        System.out.println(ans);
        sc.close();
    }
}
