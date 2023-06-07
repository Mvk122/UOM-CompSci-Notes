# Primality_Testing
* For any given number $n$, the chance that it is prime is $\frac{1}{ln(n)}$
* This means that to find a 1024 bit prime, it will take $ln(2^{1024}) ≈ 710$ attempts to find a prime on average.
* Hence the difficulty of finding a prime depends on the difficulty of checking whether a random number is prime.

## Checking If A Number Is Prime
### Brute Force Approach
* Check for every number smaller than the prime number if it divides the prime number.
* Exit the loop once the number 1 is reached.
* This can be optimized by starting at $y= \sqrt{x}$.
* The time complexity is $O(2^{n/2})$ where $n$ is the number of bits in $x$.
```python
def isPrime(x):
	y = x - 1
	while y > 0:
		if y / x == 0:
			break
		y = y - 1
	if y == 1: 
		return True
	return False
```
### Fermat's Little Theorem
* If p is prime and x is an integer where $x\: mod \: p ≠ 0$ then $x^{p-1} = 1 (mod\: p)$. 
* Hence if we pick $x$ at random and $x^{p-1} ≠ 1 (mod\: p)$ then $p$ is not prime and we can rule it out.
* However, the inverse is not true, just because $x^{p-1} = 1 (mod\: p)$, it does not mean $p$ is prime, and in the case of `carmichael numbers`, they will always equal 1 mod n for all x.
* Hence we can use fermat's little theorem to narrow down the amount of numbers that expensive prime searching is done for however it is not foolproof.

## Randomized Primality Testing
```python
def primality_test(n, t, x):
	for i in range(t):
		x = random.randint()
		if witness(x ,n):
			return True
	return False
```
* Uses the above principle with a witness function $witness(x, n)$ wherein:
	* If n is prime then witness returns false.
	* If n is composite (not prime) then it can return false with probability $q< 1$ eg can return either true or false.
* We can run the algorithm on many values of x to get more confidence in our witness function.
* The amount of times we need to run the algorithm, $t$ can be calculated with:
$$
t = \lceil\frac{k}{log_2(\frac{1}{q})}\rceil
$$
* Where $q$ is the chance that the function returns false given that the number is composite. and $k$ is the confidence parameter we want to satisfy. (How confident we want to be in the result).