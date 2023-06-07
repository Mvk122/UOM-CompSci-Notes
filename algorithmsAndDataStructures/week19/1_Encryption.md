# El Gamal Encryption
* Private/Public key cryptography that is easy to compute but very difficult to get the inverse of.
* It is based on the observation that in the equation, $y = a^b mod(p)$:
	* It is easy to compute y.
	* But it is very difficult to find `b`, even given` y, a, p`.

## Calculating Modulo using Division
* Using the example $23 mod 20$
1. Divide the first number by the second, $23/20 = 1.15$.
2. Remove the number before the decimal, leaving $0.15$.
3. Multiply this result by the second number, $0.15 * 20 = 3$
4. The answer is thus $3$.

## Euclid's Algorithm for Greatest Common Divisor
* Used in El Gamal Encryption as 2 numbers can be proved to be `relatively prime` if their Greatest Common Divisor is $1$.
* The algorithm is as such:
```python
def gcd(a,b):
	if b == 0:
		return a
	else:
		r = mod(a,b) #equivalent to a mod b
		return gcd(b,r)
```

## Multiplicative Inverses
* A multiplicative inverse is an integer $x$ wherein $a*x\:mod\:b = 1$.
* They do not always exist but will always exist for all numbers except in the case of $0\: mod\: k$ where $k$ is a prime number. (i.e all the numbers less than the prime number)

## Generators and Primitive Roots
* $Z_n^*$ is the set of numbers less than $n$ that have multiplicative inverses modulo n.
* A generator is a number that can be used to generate $Z_n^*$ for a given prime number.
* Eg 3 is a generator for 7 as there are 6 values (its order) before the results of $3^n\: mod\: 7$ start looping for increasing values of n.
* There will always be a generator for any given prime number.
* Generators are also known as `primitive roots`


## Fast Modular Exponentiation
* An algorithm that can calculate $y = a^p mod(n)$ with a time complexity `O(number_of_bits(p))`
```python
def fast_exponentiation(a, p, n):
	if p == 0:
		return 1
	if p % 2 == 0: # If it is even
		t = fast_exponentiation(a, p/2, n)
		return mod(t**2, n)
	else:
		t = fast_exponentiation(a, (p-1)/2, n)
		return mod(a * mod(t**2, n), n)
```

## Discrete Logarithm
* The discrete logarithm of an integer $y^b$ is $x$ in the equation:
$$
b^x = y\:mod\:n
$$
* There is no fast algorithm for computing discrete logarithms.

## Calculating Multiplicative Inverses
```python
# This algorithm returns the GCD as well as i and j where gcd(a,b) = ia + jb
# i is the multiplicative inverse of a
def multiplicative_inverse(a, b):
	if b == 0:
		return (a, 1, 0)
	else:
		q = mod(a,b)
		r = int((a-q)/b)
		d, i, j = multiplicative_inverse(b, mod(a,b))
		return (d, j, i - (j * r))
```

## Algorithm for El Gamal Encryption
1.  Using a public key, $(p, g , y)$ and encrypting a number $M$.
	* $p$ is a prime number.
	* $g$ is a primitive root of $p$.
	* $x$ which will not be sent is the private key.
	* $y$ is a result of using the private key $x$ where $y = g^x\:mod\:p$ 
* To encrypt, pick a random integer $k$ that is relatively prime to $p-1$ and send $(a,b)$ where:
	* $a = g^k\:mod\:p$
	* $b = My^k\:mod\:p$
* To decrypt, get the result of $a^x\:mod\:p$,  setting it as $k$ then the decrypted result is `multiplicative_inverse(k, p) * b`