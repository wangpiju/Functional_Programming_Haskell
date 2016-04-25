#Simple Recursive functions

Implement the well-known power function in two different new ways. The power function takes two arguments n and k and computes nk. Your implementation only has to work for non-negative integer k. The following is a straightforward implementation of this function:

  power :: Int -> Int -> Int
  power n k | k < 0 = error "power: negative argument"
  power n 0 = 1
  power n k = n * power n (k-1)
You will implement two more ways in this part.

a. Use the standard Haskell function product, which calculates the product (multiplication) of all elements in a list. 
To calculate power n k, first construct a list with k elements, all being n, and then use "product". 
Implement this idea as a Haskell function power1:: Int -> Int -> Int. 

b. There is a different approach to calculating the power function uses less computing steps: to calculate power n k:

If k is even, we use $(n^2)^{k/2}$
If k is odd, we use $n \times (n^{k-1})$
Implement this idea as a Haskell function power2. (Hint: Use the standard Haskell functions even and/or odd)

a.
power1 :: Int -> Int -> Int
power1 n k | k < 0 = error "power: negative argument"
power1 n 0 = 1
power1 n k = product $ replicate k n

b.
power2 :: Int -> Int -> Int
power2 n k | k < 0 = error "power: negative argument"
power2 n 0 = 1
power2 n k = 
	if even k 
	then power2 (n^2) (div k 2)
	else n * power2 n (k-1)
