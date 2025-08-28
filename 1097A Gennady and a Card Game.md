# 🃏 Gennady and a Card Game 
[**Codeforces Problem 1097A**](https://codeforces.com/problemset/problem/1097/A)

Gennady lives a peaceful life running a hotel in the countryside. His favorite card game, *Mau-Mau*, is a highlight for tourists — and now, he wants to know if you'd be a good playing partner.

This simple program checks if a player can play at least one card from their hand based on the rules of Mau-Mau.

## 📝 Problem Description

To play Mau-Mau, you use a standard 52-card deck. Each card has:
- A **rank**: `2, 3, 4, 5, 6, 7, 8, 9, T, J, Q, K, A`
- A **suit**: `D (Diamonds), C (Clubs), S (Spades), H (Hearts)`

**Rules to play a card:**
- A card from your hand can be played **only if it matches either the rank or the suit** of the card currently on the table.

### Input

- First line: A string of 2 characters — the card on the table.
- Second line: Five strings, each 2 characters long — the five cards in your hand.
- All cards are unique.

### Output

- Print `"YES"` (case-insensitive) if you can play at least one card.
- Print `"NO"` otherwise.

### Examples

#### Example 1:
Input:
AS
2H 4C TH JH AD

Output:
YES

#### Example 2:
Input:
2H
3D 4C AC KD AS

Output:
NO

#### Example 3:
Input:
4D
AS AC AD AH 5H

Output:
YES

## 🧠 Logic

Compare each of the 5 cards in hand with the table card. If **either the rank or the suit** matches, print `"YES"`. If no such card exists, print `"NO"`.

##  Sample Code (Java)

```java

import java.util.*;

public class Main {
    public static final void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String table = sc.next();

        String out = "NO";
        for(int i=0; i<5; i++){
            String str = sc.next();
            if(table.charAt(0) == str.charAt(0) 
            || table.charAt(1) == str.charAt(1)) {
                out = "YES";
                break;
            }
        }
        System.out.println(out);
        sc.close();
    }
}
