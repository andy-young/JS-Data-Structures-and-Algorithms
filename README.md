# JS-Data-Structures-and-Algorithms

## Number Algorithms

One of the most discussed algorithms involving numbers is for testing whether a number is a prime number.

### Primality Test

A primality test can be done by iterating from 2 to *n*, checking wheter modulus division (remainder) is equal to zero.

```js
function isPrime(n) {
    if (n <=1) {
        return false;
    }

    // check from 2 to n - 1
    for (let i=2; i<n; i++) {
        if (n%i == 0) return false;
    }
    return true;
}
```

[JS Visualizer 👉🏻](https://pythontutor.com/javascript.html#code=function%20primality%28n%29%20%7B%0A%20%20%20%20if%20%28n%20%3C%3D%201%29%20return%20false%3B%0A%20%20%20%20for%20%28let%20i%20%3D%202%3B%20i%20%3C%20n%3B%20i%2B%2B%29%20%7B%0A%20%20%20%20%20%20%20%20if%20%28n%20%25%20i%20%3D%3D%200%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20return%20false%3B%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20return%20true%3B%0A%7D%0A%0Aconsole.log%28primality%2853%29%29%3B&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D)

**Time Complexity:** O(*n*)
The time complexity is O(*n*) because this algorithm checks all numabers from 0 to *n*. This is an example of an algorithm that can be easily improved. Think about how this method iterates through 2 to *n*. Is it possible to find a pattern and make the algorithm faster? First, any myltiple of 2s can be ignored, but there is more optimization possible.

Let's list some prime numbers.
> 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 71, 73, 79, 83, 89, 97

This is difficult to notice, but all primes are of the form 6k ± 1, with the exception of 2 and 3 where *k* is some integer. Here's an example:

`5 = (6 - 1), 7 = ((1 * 6) + 1), 13 = ((2 * 6) + 1) etc`

Also realize that for testing the prime number *n*, the loop only has to test until the square root of *n*. This is because if the square root of *n* is not a prime number, *n* is not a prime number by mathematical definition.

```js
function isPrime(n) {
    if (n <= 1) return false;
    if (n <= 3) return true;

    // This is checked so that we can skip middle five numbers in below loop
    if (n%2 == 0 || n%3 == 0) return false;

    for (let i=5; i*i<=n; i+=6) {
        if (n%i == 0 || n%(i+2) == 0) return false;
    }

    return true
}
```

**Time Complexity:** O(*sqrt*(*n*))

### Prime Factorization

Another useful agorithm to understand is for  determining prime factorization of a number...
