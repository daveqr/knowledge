# Matrices


A matrix is a mathematical structure that consists of an ordered rectangular array of numbers, symbols, or expressions, organized into rows and columns. It is a fundamental concept in mathematics and has numerous applications in various fields, including linear algebra, physics, computer science, and engineering.

1. **Rows and Columns**: A matrix is typically represented by enclosing its elements within square brackets or vertical bars. The horizontal elements within the same row are separated by spaces or commas, while vertical elements within the same column are separated by line breaks or semicolons. For example:

	```
	| 1  2  3 |
	| 4  5  6 |
	```
	
1. **Order or Size**: The order or size of a matrix is specified as the number of rows by the number of columns. In the example above, the matrix is of order 2x3 (two rows and three columns).

1. **Elements**: The individual values or entries within a matrix are referred to as elements. In the example, the elements are the numbers 1, 2, 3, 4, 5, and 6.

1. **Types of Matrices**: Matrices can take various forms and have specific names based on their characteristics. Some common types of matrices include:

	* Row Matrix: A matrix with a single row and multiple columns.
	* Column Matrix: A matrix with a single column and multiple rows.
	* Square Matrix: A matrix with the same number of rows and columns (e.g., a 3x3 matrix).
	* Identity Matrix: A square matrix with ones on the main diagonal (from top-left to bottom-right) and zeros elsewhere.
	* Zero Matrix: A matrix where all elements are zero.
	* Scalar Matrix: A square matrix with a constant value on the main diagonal and zeros elsewhere.

1. **Matrix Operations**: Matrices can be operated on in various ways, including addition, subtraction, multiplication, and division.

## Operations

### Addition and Subtraction

These operations are performed element-wise, meaning that corresponding elements in the same positions of the two matrices are added or subtracted to form a new matrix. The key requirement for matrix addition is that the matrices must have the same dimensions (i.e., the same number of rows and columns).


```
public static int[][] addMatrices(int[][] arr1, int[][] arr2) {
    int rows = arr1.length;
    int cols = arr1[0].length;

    int[][] addedArr = new int[rows][cols];

    for (int i = 0; i < arr1.length; i++) {
        for (int j = 0; j < arr1[i].length; j++) {
            int val1 = arr1[i][j];
            int val2 = arr2[i][j];
            // or - for subtraction
            addedArr[i][j] = val1 + val2;
        }
    }

    return addedArr;
}
```

### Multiplication

Matrix multiplication is a more complex operation compared to addition and subtraction. It involves multiplying elements from one matrix with elements from another matrix according to specific rules. Matrix multiplication is not element-wise; instead, it follows a well-defined procedure that combines rows and columns to produce a new matrix. The number of columns in the first matrix must match the number of rows in the second matrix for multiplication to be defined.

Algorithm:

Multiply rows of the first matrix with columns of the second matrix to compute the elements of the resulting matrix.

```
| 1  2 |   | 3  4 |   | 1*3+2*7  1*4+2*8 |   | 17  20 |
| 5  6 | x | 7  8 | = | 5*3+6*7  5*4+6*8 | = | 47  56 |
```

## Determinant

The determinant is a single scalar value that represents a property of a square matrix. It provides important information about the matrix, such as whether the matrix is invertible (non-singular) or singular, and it plays a crucial role in various mathematical and engineering applications.

One use of the determinant is to determine whether the matrix is invertible (non-singular) or singular. 

* **Invertible matrices** have an inverse.  If you multiply an invertible matrix by its inverse, you get the identity matrix. These matrices have a nonzero determinant.
* **Singular matrices** do not have an inverse. In other words, if A is a singular matrix, there is no matrix B such that A * B = B * A = I, where I is the identity matrix. Singular matrices have a determinant of zero.

### Determinant Calculation

#### 2x2 matrix

```
| a  b |
| c  d |

det(A) = (a * d) - (b * c)
```

#### 3x3 matrix

```
| a  b  c |
| d  e  f |
| g  h  i |

det(A) = a(ei - fh) - b(di - fg) + c(dh - eg)
```

#### Examples

```
2x2
============

| 3  4 |
| 2  1 |

det(A) = (3 * 1) - (4 * 2)
det(A) = 3 - 8
det(A) = -5

3x3
============

| 2  0  1 |
| 1  3  4 |
| 0 -1  2 |

det(A) = 2(3*2 - 4*(-1)) - 0(1*2 - 4*0) + 1(1*(-1) - 3*0)
det(A) = 2(6 + 4) - 0(2 - 0) + 1(-1 - 0)
det(A) = 2(10) - 0(2) + 1(-1)
det(A) = 20 - 0 - 1
det(A) = 19

```