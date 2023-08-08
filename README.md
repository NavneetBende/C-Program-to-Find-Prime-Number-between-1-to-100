# C-Program-to-Find-Prime-Number-between-1-to-100

Prime Number between 1 to 100 in C
Here, on this page, we will discuss the program to find the prime numbers between 1 to 100 in C.

Generally this program is asked as Write a Program to print Prime Numbers from 1 to 100 in C

Prime number
Methods Discussed in page
We have discussed the following methods

Basic checking prime by only checking first n
Basic checking prime by only checking first n/2 divisors
Checking prime by only checking first √n divisors
Checking prime by only checking first √n divisors, but also skipping even iterations.
Method 1
Set lower bound = 1, upper bound = 100
Run a loop in the iteration of (i) b/w these bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
Here we use the usual method to check prime. If given number is prime then we print it else we move ahead to the next number and check if that is prime and keep going till 100
Code
#include <stdio.h>

int checkPrime(int num)
{
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        return 0;
    }
    else{   
    // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways. 
    // Example 36 wont be divisible by anything b/w 19-35
        int x = num/2;
        for(int i = 2; i <=x; i++)
        {
            if(num % i == 0)
            {
                return 0;
            }
        }
    }
    // the number would be prime if we reach here
    return 1;
}

int main()
{
    int a = 1, b = 100;
    
    for(int i=a; i <= b; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N^2)
//Space Complexity O(1)
Output
2 3 4 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 
While loop in C
Method 2
Run a loop in the iteration of (i) b/w 1 and 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to the next iteration
Method used to check prime
Here we use the usual method to check prime. We however check the divisibility only till num/2.

As the range(num/2 + 1, num) won't be divisible anyways. Example 36 won't be divisible by anything b/w 19-35
Code
#include<stdio.h>

int checkPrime(int num)
{
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        return 0;
    }
    else{   
    // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways. 
    // Example 36 wont be divisible by anything b/w 19-35
        int x = num/2;
        for(int i = 2; i < x; i++)
        {
            if(num % i == 0)
            {
                return 0;
            }
        }
    }
    // the number would be prime if we reach here
    return 1;
}

int main()
{
    
    for(int i=1; i <= 100; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N^2)
//Space Complexity O(1)
Output
2 3 4 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 
Related Pages
Count possible decoding of a given digit sequence

Find the prime numbers between 1 to 100

Calculate the number of digits in an integer

Convert digit/number to words

Counting number of days in a given month of a year

Method 3
The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has better time complexity of O(√N)

Run a loop in the iteration of (i) b/w 1 and 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
A number n is not a prime if it can be factored into two factors a & b:
n = a * b

Now a and b can't be both greater than the square root of n, since then the product a * b would be greater than sqrt(n) * sqrt(n) = n.

So in any factorization of n, at least one of the factors must be smaller than the square root of n, and if we can't find any factors less than or equal to the square root, n must be a prime.

So we only need to run loop till sqrt(n) and not n or n/2
Code
#include<stdio.h>
#include<math.h>

int checkPrime(int num)
{
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        return 0;
    }
    else{   
    // A number n is not a prime, if it can be factored into two factors a & b:
    // n = a * b

    /*Now a and b can't be both greater than the square root of n, since
    then the product a * b would be greater than sqrt(n) * sqrt(n) = n.
    So in any factorization of n, at least one of the factors must be
    smaller than the square root of n, and if we can't find any factors
    less than or equal to the square root, n must be a prime.
    */
        for(int i = 2; i < sqrt(num); i++)
        {
            if(num % i == 0)
            {
                return 0;
            }
        }
    }
    // the number would be prime if we reach here
    return 1;
}

int main()
{
    
    for(int i=1; i <= 100; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N√N)
//Space Complexity O(1)

// This method is obviously  faster as has better time complexity
Output
2 3 4 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 
While loop in C
Method 4
The outer logic remains the same. Only the method to check prime changes to make code more optimized. Has same time complexity of O(√N).

But makes around half lesser checks

Run a loop in the iteration of (i) b/w 1 to 100 bounds.
For each, i check if its prime or not using function checkPrime(i)
If i is prime print it else move to next iteration
Method used to check prime
This method uses the assumption that –

We can simply check all divisors between [2, √num]
2 is the only even prime number
We can skip all even iterations in the loop
Code
#include<stdio.h>
#include<math.h>

int checkPrime(int n)
{
    // 0 and 1 are not prime numbers
    // negative numbers are not prime
    if (n <= 1)
        return 0;

    // special case as 2 is the only even number that is prime
    else if (n == 2)
        return 1;

    // Check if n is a multiple of 2 thus all these won't be prime
    else if (n % 2 == 0)
        return 0;

    // If not, then just check the odds
    for (int i = 3; i <= sqrt(n); i += 2)
    {
        if (n % i == 0)
            return 0;
    }
    
    return 1;
}

int main()
{
    
    for(int i=1; i <= 100; i++){
        if(checkPrime(i))
            printf("%d ",i);
    }
 
    return 0;
}
//Time Complexity: O(N√N)
//Space Complexity O(1)

// This method is obviously faster as makes around half lesser comparision due skipping even iterations in the loop
Output
2 3 4 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 
