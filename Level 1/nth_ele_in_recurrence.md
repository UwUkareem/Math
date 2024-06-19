# usage 

- we use matrix expo to calculate the nth element in any recurrence relation

# main idea

- https://zobayer.blogspot.com/2010/11/matrix-exponentiation.html

# implementation

- we initial the square matrix and forming it
- we initial the recur_matrix and forming it , its [1][]
- if we need the nth element we use matrix_expo by : (square_matrix ^ n)
- then we use mul (square_matrix ^ n) * recur_matrix
- the result is the frist element

# time complexity
  ### dim^3 * log(n)

# code

matrix_expo code
