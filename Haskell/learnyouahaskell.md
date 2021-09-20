# Haskell Beginner Level Notes 
[View Source Reference](http://learnyouahaskell.com/)

## 1. Introduction
- Haskell is a statically typed, purely functional, lazy programming language
- The interactive mode is invoked by typing in `ghci` at your prompt
- If you have defined some functions in a file called, say, `myfunctions.hs`, you load up those functions by typing in `:l myfunctions`

## 2. Starting Out
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
  - `length` takes a list and returns its length
    ```haskell
    ghci> length [5,4,3,2,1]  
    5 
    ```
  - `null` checks if a list is empty
    ```haskell
    ghci> null [1,2,3]  
    False  
    ghci> null []  
    True  
    ```
  - `reverse` reverses a list
    ```haskell
    ghci> reverse [5,4,3,2,1]  
    [1,2,3,4,5]
    ```
  - `take` extracts specified number of elements from the beginning of the list
    ```haskell
    ghci> take 3 [5,4,3,2,1]  
    [5,4,3]  
    ghci> take 1 [3,9,3]  
    [3]  
    ghci> take 5 [1,2]  
    [1,2]  
    ghci> take 0 [6,6,6]  
    []  
    ```
  - `drop` drops the number of elements from the beginning of a list
    ```haskell
    ghci> drop 3 [8,4,2,1,5,6]  
    [1,5,6]  
    ghci> drop 0 [1,2,3,4]  
    [1,2,3,4]  
    ghci> drop 100 [1,2,3,4]  
    [] 
    ```
  - `maximum` takes a list of stuff that can be put in some kind of order and returns the biggest element. `minimum` returns the smallest
    ```haskell
    ghci> minimum [8,4,2,1,5,6]  
    1  
    ghci> maximum [1,9,2,3,4]  
    9   
    ```
  - `sum` takes a list of numbers and returns their sum
  - `product` takes a list of numbers and returns their product
    ```haskell
    ghci> sum [5,2,1,6,3,2,5,7]  
    31  
    ghci> product [6,2,1,2]  
    24  
    ghci> product [1,2,5,6,7,9,2,0]  
    0   
    ``` 
  - `elem` takes a thing and a list of things and tells us if that thing is an element of the list
    ```haskell
    ghci> 4 `elem` [3,4,5,6]  
    True  
    ghci> 10 `elem` [3,4,5,6]  
    False 
    ```
### Ranges
- To make a list containing all the natural numbers from 1 to 20, you just write `[1..20]`
  ```haskell
  ghci> [1..20]  
  [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]  
  ghci> ['a'..'z']  
  "abcdefghijklmnopqrstuvwxyz"  
  ghci> ['K'..'Z']  
  "KLMNOPQRSTUVWXYZ"
  ```
- Ranges can also specify a step
  ```haskell
  ghci> [2,4..20]  
  [2,4,6,8,10,12,14,16,18,20]  
  ghci> [3,6..20]  
  [3,6,9,12,15,18]   
  ```
- Some functions can be used to produce infinite sets
  - `cycle` takes a list and cycles it into an infinite list
    ```haskell
    ghci> take 10 (cycle [1,2,3])  
    [1,2,3,1,2,3,1,2,3,1]  
    ghci> take 12 (cycle "LOL ")  
    "LOL LOL LOL "   
    ```
  - `repeat` takes an element and produces an infinite list of just that element
    ```haskell
    ghci> take 10 (repeat 5)  
    [5,5,5,5,5,5,5,5,5,5] 
    ```
  - `replicate` function also has a similar effect
    ```haskell
    ghci> replicate 3 10
    [10,10,10]
    ```
### List Comprehension
- List comprehensions are useful for creating lists with elements that follow the given constraints
- The following line will create a list of the first ten even numbers
  ```haskell
  ghci> [x*2 | x <- [1..10]]  
  [2,4,6,8,10,12,14,16,18,20] 
  ```
- We can add a condition (or a pedicate) that go after the binding parts and are separated from them by a comma
  ```haskell
  ghci> [x*2 | x <- [1..10], x*2 >= 12]  
  [12,14,16,18,20]  
  ```
- Not only can we have multiple predicates in list comprehensions (an element must satisfy all the predicates to be included in the resulting list), we can also draw from several lists
  ```haskell
  ghci> [ x*y | x <- [2,5,10], y <- [8,10,11]]  
  [16,20,22,40,50,55,80,100,110]
  ghci> [ x*y | x <- [2,5,10], y <- [8,10,11], x*y > 50]  
  [55,80,100,110]
  ```
### Tuples
- We use tuples when it is known in advance how many components some piece of data should have. Tuples are much more rigid because each different size of tuple is its own type.
- Tuples are surrounded by `()` 
  ```haskell
  ("Christopher", "Walken", 55)
  ```
- Here are two useful functions that operate on pairs
  - `fst` takes a pair and returns its first component
    ```haskell
    ghci> fst (8,11)  
    8  
    ghci> fst ("Wow", False)  
    "Wow" 
    ```
  - `snd` takes a pair and returns its second component
    ```haskell
    ghci> snd (8,11)  
    11  
    ghci> snd ("Wow", False)  
    False  
    ```
- `zip` takes two lists and then zips them together into one list by joining the matching elements into pairs
  ```haskell
  ghci> zip [1,2,3,4,5] [5,5,5,5,5]  
  [(1,5),(2,5),(3,5),(4,5),(5,5)]  
  ghci> zip [1 .. 5] ["one", "two", "three", "four", "five"]  
  [(1,"one"),(2,"two"),(3,"three"),(4,"four"),(5,"five")]  
  ```
## Types and Typeclasses
- The type of any expression can be inspected using `:t` command on `ghci`
  ```haskell
  ghci> :t 'a'  
  'a' :: Char  
  ghci> :t True  
  True :: Bool  
  ghci> :t "HELLO!"  
  "HELLO!" :: [Char]  
  ghci> :t (True, 'a')  
  (True, 'a') :: (Bool, Char)  
  ghci> :t 4 == 5  
  4 == 5 :: Bool 
  ```
  > Note : `::` is read as "has type of"
- When writing our own functions, we can choose to give them an explicit type declaration
  ```haskell
  removeNonUppercase :: [Char] -> [Char]  
  removeNonUppercase st = [ c | c <- st, c `elem` ['A'..'Z']]   
  addThree :: Int -> Int -> Int -> Int  
  addThree x y z = x + y + z  
  ```
- In case of ambiguous situations `::` can be used to specify the type
  ```haskell
  Prelude> 4
  4
  Prelude> 4 :: Float
  4.0
  Prelude> 
  ```
- Some common types are 
  - `Int`
  - `Integer`
  - `Float`
  - `Double`
  - `Bool`
  - `Char`
- A typeclass is one level abstraction above types
- Examples of typeclasses being 
  - `Eq`
  - `Ord`
  - `Show`
  - `Read`
  - `Enum`
  - `Bounded`
  - `Num`
  - `Integral`
  - `Floating`
- `Bounded` types have upper and lower bound
  ```haskell
  ghci> minBound :: Int  
  -2147483648  
  ghci> maxBound :: Char  
  '\1114111'  
  ghci> maxBound :: Bool  
  True  
  ghci> minBound :: Bool  
  False 
  ```
- A very useful function for dealing with numbers is `fromIntegral`
  ```haskell
  ghci> :t fromIntegral  
  fromIntegral :: (Integral a, Num b) => a -> b
  ghci> fromIntegral (length [1,2,3,4]) + 3.2
  7.2
  ```
  > Note : We had to use `fromIntegral` because `length` returns `Int` which is not addable with a float. So we converted it into a more genaral `Num`

