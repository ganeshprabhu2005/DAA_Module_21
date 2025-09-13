# EX 3D Pattern Matching
## DATE:17-07-2025
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.



## Algorithm

1. Take input `txt` (text) and `pat` (pattern) to search for.  
2. Compute the Longest Prefix Suffix (LPS) array for the pattern to preprocess repeating sub-patterns.  
3. Initialize pointers `i = 0` (for text) and `j = 0` (for pattern).  
4. Loop through the text while the remaining characters in text are enough for a possible match.  
5. If `pat[j] == txt[i]`, increment both `i` and `j`.  
6. If `j == M` (end of pattern reached), a match is found — print the index `i - j`.  
7. Then, reset `j` using `lps[j-1]` to continue searching for next occurrences.  
8. If a mismatch occurs and `j != 0`, reset `j = lps[j-1]`; else increment `i`.  
9. Repeat until the entire text has been searched.

## Program:
```
Program to implement the Pattern Matching.
Developed by: GANESH PRABHU J
Register Number: 212223220023
```
```PY
def KMPSearch(pat, txt):
    M = len(pat)
    N = len(txt)
    lps=[0]*M
    j=0
    computeLPSArray(pat,M,lps)
    i=0
    
    while(N-i)>=(M-j):
        if pat[j]==txt[i]:
            i+=1
            j+=1
        if j==M:
            print("Found pattern at index",i-j)
            j=lps[j-1]
        elif i<N and pat[j]!=txt[i]:
            if j!=0:
                j = lps[j-1]
            else:
                i+=1
    
def computeLPSArray(pat, M, lps):
    len = 0 
 
    lps[0] 
    i = 1
    while i < M:
        if pat[i]== pat[len]:
            len += 1
            lps[i] = len
            i += 1
        else:
            if len != 0:
                len = lps[len-1]
            else:
                lps[i] = 0
                i += 1
txt = input()                      
pat = input()
KMPSearch(pat, txt)
```
## Output:

![image](https://github.com/user-attachments/assets/8a158d6f-b56b-482d-80f9-dca994e37f3e)

## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
