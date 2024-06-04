---
title: Matrix
Date created: 2024-06-02 21:53
Aliases: 2D Array
tags: 
  - Public
---

A matrix is a two-dimensional array or table, which can be represented as a grid of rows and columns. A single value which is an intersection of a row and a column is called a cell, which is usually accessed by row and column indices

### Corner Cases
- Empty matrix, one of the arrays of length 0
- 1 by 1 matrix
- one row/ one column matrix

## Techniques

### Creating an `n` by `m` Matrix
Creating a matrix of specified dimensions is often useful when dealing with graph traversal or dynamic programming.

```Java
int[][] matrix = new int[n][m];
```

```python
new_matrix = [[0 for _ in range(len(matrix[0]))] for _ in range(len(matrix))]
```
### Copying an Existing Matrix
```Java
int [][] newMatrix = new int[matrix.length][]
for(int i=0; i<matrix.length;i++) {
	newMatrix[i] = matrix[i].clone();
}
```

```python
copied_matrix = [row[:] for row in matrix]
```

### Transposing a Matrix
Transposing a matrix is done by interchanging its rows into columns. It can be useful if you have to do an operation on both rows and columns, you can then create one function, transpose the matrix and run it again.
```java
int[][] result = new int[mat[0].length][mat.length];
for (int i = 0; i < mat.length; ++i) {
	for (int j = 0; j < mat[0].length; ++j) {
		result[j][i] = mat[i][j];
	}
}
```


```python
transposed_matrix = zip(*matrix)
```