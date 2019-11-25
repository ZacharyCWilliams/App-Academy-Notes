# Interview Prep

Algorithms & Interview prep notes

## Types Of Math Functions

Good Small Growth

1. **Constant**: `f(n) = 1` | Not dependent on input
2. **Logarithmic**: `f(n) = log(n)` | Reverse exponent (log2^16 = 4 because 2 * 2 * 2 * 2 = 16)
3. **Linear**: `f(n) = n` | 
4. **Loglinear**: `f(n) = n * log(n)` | 
5. **Polynomial**: `f(n) = N^c` | base n raised to a constant (n^2, n^3, n^4 etc.)
6. **Exponential**: `f(n) = C^n` | a constant base raised to an exponential (2^n, 3^n)
7. **Factorial**: `f(n) = n!` | 4! => 4 * 3 * 2 * 1

Bad Fast Growth

## Big O Notes

 In this section we'll explore how to analyze the efficiency of algorithms in terms of their speed (time complexity) and memory consumption (space complexity).

 The question we MUST ask ourselves the golden question, which is, **how does our performance scale?** In other words:

 ```
Will your code still be performant if we increase the size of the input? For example, sorting 3 numbers is trivial; but how about a million numbers?
 ```




