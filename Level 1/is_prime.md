# main idea

- we can get all divisors of a number by iterating sqrt(n),
   if we found a number divisible by n we can get the other divisor (n/number)
- even numbers "except 2" aren't prime so all the even divisors aren't prime

# implementation

- check if number is even "except 2"
- iterate through the odd divisors until sqrt(n)

# time complexity
  ### Sqrt(n)
