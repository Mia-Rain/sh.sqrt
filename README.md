```
---
# sh.sqrt
-- Square Root (√) in pure POSIX sh
---- various methods included; see
----- https://en.wikipedia.org/wiki/Methods_of_computing_square_roots 
---
# Limitations of POSIX sh
-- Unfortunately POSIX sh has zero support for non-whole numbers
-- Thus numbers which do /not/ have whole number square roots
---- /CANNOT/ be calculated
-- This limitation cannot be bypassed without implementing
---- float points pure POSIX sh, which I have tried and failed at
---
# Babylonian Method
-- The Babylonian method is the first to be implemented
-- Since sh can only actively work with whole numbers on its own
-- The method is actually quite accurate
-- However (obv) a break down occurs when numbers without 
---- whole Square Roots are inputed, however;
---- the algorithm should/has (have) been adjusted to detect when it 
---- enters and endless loop, and should produce the closest whole number
-- This method requires a starting seed; POSIX sh however lacks $RANDOM
-- thus psh-prng is used by this method; one will have to clone with
---- `--recursive` to pull in the submodule
---
# Mia Method (Miterate)
-- The Mia method works for all numbers >4 with whole digit square roots
-- It works by iterating over every number from 2 -> S/3 until it reaches 
---- the square root of S
-- The square root of 4 has to be hard coded since 4/3 produces
---- 1.333[...] which is < the square root (2)
---
# Comparison (Babylonian and Miterate)
-- Over 12 iterations; calculating the square root of 144
---- Babylonian Method: 0.1625 seconds (real time)
---- Mia Method: 0.0075 seconds (real time)
-- However it should be noted that that Babylonian Method
---- (when not restricted by sh) can calculate decimal points
```
