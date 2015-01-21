# An Adventure in Approximation
## with Lambda expressions and Closures

We start with the basic approximation of square roots, as described in the book/lectures. It goes something like this

```scheme
(define (sqrt guess x)
	(if (good-enough? guess x)
		guess
		(sqrt (improve-guess guess x) x)
	)
)
```

Now, we need to provide the two functions `good-enough?` and `improve-guess`, and their supporting functions `abs` and `avg`. The whole think winds up looking like this

```scheme
(define (abs x)
	(if (< x 0)
		(- x)
		x))
(define (avg a b)
	(/ (+ a b) 2))
(define (good-enough? guess x)
	(< (abs (- guess (/ x guess))) 0.0001))
(define (improve-guess guess x)
	(avg guess (/ x guess)))
(define (sqrt guess x)
	(if (good-enough? guess x)
		guess
		(sqrt (improve-guess guess x) x)
	)
)
```
