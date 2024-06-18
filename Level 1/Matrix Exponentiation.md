# usage 

- Given matrix A and power n we need to calc (A^n)

# main idea

- we just use binary expo and simple matrices multiplication

# time complexity
  ###  (dim^3)*log(n)
  (dimension of square matrix)^3  *  log(power)


# code

```cpp

// result store in I matrix
// read dimension (dim) & power (n) & elements of matrix (arr)
int dim,n;
const int N = 105;
int arr[N][N], I[N][N];

// multiplication of 2 matrices and result in a
void mul (int a[][N], int b[][N]){
    int res[dim+2][dim+2];
    for (int i = 0; i < dim; ++i) {
        for (int j = 0; j < dim; ++j) {
            res[i][j]=0;
            for (int k = 0; k < dim; ++k) {
                res[i][j] += ( a[i][k] * b[k][j] );
            }
        }
    }

    // save res in I (here named a)
    for (int i = 0; i < dim; ++i) {
        for (int j = 0; j < dim; ++j) {
            a[i][j] = res[i][j];
        }
    }
}

void matrix_expo(){
    // initalize identity matrix
    for (int i = 0; i < dim; ++i) {
        for (int j = 0; j < dim; ++j) {
            if(i==j)
                I[i][j]=1;
        }
    }

    // binary_expo
    while (n) {
        if (n & 1) {
            mul(I, arr);
            n--;
        }
        mul(arr, arr);
        n >>= 1;
    }

}

```
