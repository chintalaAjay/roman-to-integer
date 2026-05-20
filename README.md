# Roman to Integer

## Problem Statement
Convert a Roman numeral string into its corresponding integer value.

Problem Link:  
https://leetcode.com/problems/roman-to-integer/

---

# Approach

I solved this problem using a Greedy Approach with two arrays:

- One array stores Roman symbols.
- Another array stores their corresponding integer values.

```java
String roman[] = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

int values[] = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
Key Idea

The Roman symbols are arranged from:

Largest → Smallest

This helps handle special cases like:

CM = 900
IV = 4
IX = 9

before checking normal symbols.

Logic Used

For every Roman symbol:

Check whether the string starts with that symbol.
If yes:
Add its value to the result.
Remove that symbol from the string.
Repeat until the symbol no longer appears at the beginning.
Important Condition
while(s.indexOf(roman[i]) == 0)

This checks whether the current Roman symbol is present at the starting index of the string.

Example:

s = "CMXCIV"
"CM" found at index 0
Add 900
Remove "CM"
Remaining string becomes "XCIV"
Dry Run

Input:

MCMXCIV
Step 1
M found → add 1000
Remaining = CMXCIV
Step 2
CM found → add 900
Remaining = XCIV
Step 3
XC found → add 90
Remaining = IV
Step 4
IV found → add 4
Remaining = ""

Final Answer:

1994
Time Complexity
O(N)

Because every character is processed once.

Space Complexity
O(1)

Only fixed arrays are used.

Java Solution
class Solution {
    public int romanToInt(String s) {

        int values[] = {1000,900,500,400,100,90,50,40,10,9,5,4,1};

        String roman[] = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

        int res = 0;

        for(int i=0;i<roman.length;i++){

            while(s.indexOf(roman[i]) == 0){

                res += values[i];

                s = s.substring(roman[i].length());
            }
        }

        return res;
    }
}
