# Haskell Beginner Level Notes 
[View Source Reference](http://learnyouahaskell.com/)

## Introduction
- Haskell is a statically typed, purely functional, lazy programming language
- The interactive mode is invoked by typing in `ghci` at your prompt
- If you have defined some functions in a file called, say, `myfunctions.hs`, you load up those functions by typing in `:l myfunctions`

## Starting Out
- The `succ` function takes anything that has a defined successor and returns that successor
```haskell
ghci> succ 8 
9
```
- The functions `min` and `max` take two things that can be put in an order. `min` returns the one that's lesser and `max` returns the one that's greater
```haskell
ghci> min 9 10  
9  
ghci> min 3.4 3.2  
3.2  
ghci> max 100 101  
101
```
- Function application has the highest precedence. ie the below expressions are equivalent
```haskell
ghci> succ 9 + max 5 4 + 1  
16  
ghci> (succ 9) + (max 5 4) + 1  
16  
```
- Prefix functions can be used as infix like so
```haskell
Prelude> div 92 10
9
Prelude> 92 `div` 10
9
```
- Some basic examples of functions 
```haskell
doubleMe x = x + x  
doubleUs x y = x*2 + y*2   
```
- If statement
```haskell
doubleSmallNumber x = if x > 100 then x else x*2   
```
- In Haskell an if statement is an expression (it always returns a value)
- It is entirely valid to use `'` in function names. We usually use `'` to either denote a strict version of a function (one that isn't lazy) or a slightly modified version of a function or a variable
```haskell
doubleSmallNumber' x = (if x > 100 then x else x*2) + 1  
```
- `"hello"` is just syntactic sugar for `['h','e','l','l','o']` Because strings are same as lists under the hood
- Two lists can be joined using the `++` operator
```haskell
ghci> [1,2,3,4] ++ [9,10,11,12]  
[1,2,3,4,9,10,11,12]  
ghci> "hello" ++ " " ++ "world"  
"hello world"  
ghci> ['w','o'] ++ ['o','t']  
"woot" 
```
> Note: `++` will have *O(n)* complexity as it has to iterate completely through the left list
- We can prepend an element to a list using  `:` (also called the cons operator) 
```haskell
ghci> 'A':" SMALL CAT"  
"A SMALL CAT"  
ghci> 5:[1,2,3,4,5]  
[5,1,2,3,4,5]  
```
> Note: `[1,2,3]` is actually just syntactic sugar for `1:2:3:[]`
- If you want to get an element out of a list by index, use `!!`
```haskell
ghci> "Steve Buscemi" !! 6  
'B'  
ghci> [9.4,33.2,96.2,11.2,23.25] !! 1  
33.2 
```
- These are some basic operations on lists
  - `head` takes a list and returns its head
  ```haskell
  ghci> head [5,4,3,2,1]  
  5 
  ```
  - `tail` takes a list and returns its tail
  ```haskell
  ghci> tail [5,4,3,2,1]  
  [4,3,2,1]
  ```
  - `last` takes a list and returns its last element
  ```haskell
  ghci> last [5,4,3,2,1]  
  1  
  ```
  - `init` takes a list and returns everything except its last element
  ```haskell
  ghci> init [5,4,3,2,1]  
  [5,4,3,2] 
  ```
-