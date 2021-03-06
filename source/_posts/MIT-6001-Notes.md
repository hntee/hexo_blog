title: 'MIT 6.001 Notes'
date: 2014-06-22 18:49:43
tags:
---

[Course Page Here](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/) 

# 1A: Overview and Introduction to Lisp

## Define a procedure:
`(define (square x) (* x x))` or `(define square (lambda (x) (* x x)))`

*The former one is a syntax sugar of the previous one.*

## Condition Expression

```lisp
(define (abs x)
  (cond ((< x 0) (-x))
      ((= x 0) 0)
      ((> x 0) x)))
```

## A square root approach

```lisp
(define (sqrt x)
  (define (improve guess x)
    (average guess (/ x guess)))
  (define (good-enough? guess x)
    (< (abs (- (square guess) x))
       .001))
  (define (try guess)
    (if (good-enough? guess)
        guess
        (try (improve guess))))
  (try 1))
```






