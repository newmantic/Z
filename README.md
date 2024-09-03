# Z


The Z-Algorithm is an efficient string-matching algorithm that computes the Z-array (or Z-function) for a given string. The Z-array is particularly useful in pattern matching, as it helps identify substrings within a string that match the prefix of the string.


Z-Array:
For a given string S of length n, the Z-array Z[i] represents the length of the longest substring starting from position i in S that matches the prefix of S.
Formally, Z[i] is the length of the longest substring starting from S[i] that is also a prefix of S.

Prefix:
A prefix of a string is any leading contiguous substring of the string. For example, the prefixes of "abc" are "", "a", "ab", and "abc".


Consider the string S = "abacaba":
Z[0] is always n because the whole string is always a prefix of itself.
Z[1] is 0 because the substring starting at S[1] ("bacaba") does not match the prefix "abacaba".
Z[2] is 1 because the substring "acaba" has "a" as a prefix.
The Z-array for "abacaba" would be [0, 0, 1, 0, 3, 0, 1].


Initialize:
Start with Z[0] = 0 and initialize variables L = 0, R = 0 that represent the current segment [L, R] where S[L:R] matches the prefix S[0:R-L].

Iterate Through the String:
For each i from 1 to n-1:
If i > R, reset L and R to i, and compare the substring starting at i with the prefix of S. Set Z[i] to the length of this match.
If i <= R, determine the value of Z[i] based on the previously computed values:
Let k = i - L.
If Z[k] < R - i + 1, set Z[i] = Z[k].
If Z[k] >= R - i + 1, extend the match beyond R and update L, R, and Z[i] accordingly.


Time Complexity
The Z-Algorithm runs in O(n) time because it processes each character of the string at most twice.

To find all occurrences of a pattern P in a text T:
Concatenate the pattern P with the text T using a special delimiter, e.g., S = P + "$" + T.
Compute the Z-array for the concatenated string S.
Identify Matches by checking if any Z[i] equals the length of the pattern P. If so, the pattern P occurs in T starting at index i - len(P) - 1.
