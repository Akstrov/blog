# Unveiling the Magic of Recursion in Computer Science

![Recursion Magic](https://res.cloudinary.com/dypuafyyu/image/upload/f_auto,q_auto/v1/blog/x0ai6wwfueuvlhkxpifo)

Procedures, just like mathematical functions, specify a value that is determined by some parameters.

But there is a difference.

A mathematical function can describe the square root like this:

```
Sqrt(x) = y / y >= 0; y^2 = x
```

But it does not tell us how to get the square root.

So the difference is: mathematical functions are concerned with declarative descriptions (What is); In Computer Science, we are concerned with imperative descriptions (How To).

So how do you compute the square root? We can use Newton's method of successive approximations.

## The Enchanting Square Root Calculation

Let's embark on an enchanting journey into the realm of square root calculations using Newton's method of successive approximations. The square root is a special case where we seek an approximation that, when squared, yields a value close to the original number.

To obtain the square root approximation using Newton's method, we employ the following formula:

```
newGuess = (guess + (x / guess)) / 2
```

The algorithm for calculating the square root can be explained as follows:

1. We start with an initial guess for the square root.
2. We improve our approximation by using the formula mentioned above. We calculate the average of the guess and the original number divided by the guess.
3. We repeat the process, using the improved guess in the next iteration.
4. We continue iterating until our approximation reaches a satisfactory level of accuracy.

Let's illustrate the process with an example. Suppose we want to find the square root of 9:

**Example: Calculating the Square Root of 9**

| Guess | Average                       |
| ----- | ----------------------------- |
| 1     | ((1 + 9/1) / 2) = 5           |
| 5     | ((5 + 9/5) / 2) = 3.4         |
| 3.4   | ((3.4 + 9/3.4) / 2) = 3.02350 |

As we continue iterating, our approximation gets closer to the actual square root of 9, which is 3.

The power of recursion shines through in this algorithm. With each iteration, we call the `sqrt-iter` function recursively, passing the improved guess as the new guess, until we reach the desired level of accuracy.

Now, let's witness the enchantment of recursion in action as we implement the square root calculation in Scheme:

```scheme
(define (sqrt x)
  (sqrt-iter 1.0 x))

(define (sqrt-iter guess x)
  (if (good-enough? guess (improve guess x))
      guess
      (sqrt-iter (improve guess x) x)))

(define (improve guess x)
  (average guess (/ x guess)))

(define (average x y)
  (/ (+ x y) 2))

(define (good-enough? guess newGuess)
  (< (abs (- guess newGuess)) (* 1.0e-20 guess)))
```

## The Marvelous Cube Root Calculation

Now, let's explore the captivating world of cube root calculation. Similar to the square root, the cube root is a special case where we desire an approximation that, when cubed, approaches the original number.

The formula for improving our guess slightly adjusts:

```
newGuess = ((2 * guess) + (x / (guess * guess))) / 3
```

Since we have already explained the algorithmic magic of recursion in the square root calculation

, implementing the cube root calculation becomes straightforward. We can utilize a similar structure with a few adjustments.

```scheme
(define (cbrt x)
  (cbrt-iter 1.0 x))

(define (cbrt-iter guess x)
  (if (good-enough? guess (improve guess x))
      guess
      (cbrt-iter (improve guess x) x)))

(define (improve guess x)
  (/ (+ (/ x (* guess guess)) (* 2 guess)) 3))
```

## Embrace the Magic of Recursion

In this sorcerer's journey, we have delved into the enchanting realms of square root and cube root calculations using the power of recursion and Newton's method of successive approximations. Witnessing the iterative refinement and the elegance of recursive calls, we have unraveled the secrets of these mystical computations.

May the spirit of recursion guide you on your own magical adventures in the realm of computer science! ✨🔮
