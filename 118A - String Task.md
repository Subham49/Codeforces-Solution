# ✂️ String Task  
[118A - String Task](https://codeforces.com/problemset/problem/118/A)


### 💡 Problem Statement

Petya is learning to code. His first programming task is to write a simple string manipulation program.

Given a string consisting of **only uppercase and lowercase Latin letters**, perform the following operations:

1. **Delete all vowels**: `A, O, Y, E, U, I` (case-insensitive)
2. **Insert a `.`** before each **remaining consonant**
3. **Convert all uppercase letters** to **lowercase**

---

### 📥 Input

- A single string `s` consisting of uppercase and lowercase Latin letters.  
- `1 ≤ |s| ≤ 100`


### 📤 Output

- A single string after applying all transformations.

---

### 🧪 Examples

#### Input
tour

#### Output
.t.r


#### Input
Codeforces

#### Output
.c.d.f.r.c.s


#### Input
aBAcAba

#### Output
.b.c.b

---

### 🧠 Logic

To solve the problem:

1. Convert all characters to **lowercase**
2. Check each character:
   - If it is a **vowel**, **skip** it
   - If it's a **consonant**, **append** `.` followed by the character to the result
3. Print the resulting string


### ✅ Java Solution

```java
import java.util.*;

public class HelloWorld {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String str = scanner.next();
        StringBuilder sb = new StringBuilder();

        for (char ch : str.toCharArray()) {
            ch = Character.toLowerCase(ch);
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' || ch == 'y') {
                continue;
            } else {
                sb.append(".").append(ch);
            }
        }

        System.out.println(sb.toString());
        scanner.close();
    }
}
