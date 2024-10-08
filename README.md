# DATE:
# EXP.No:05
# LU Decomposition 

## AIM:
To write a program to find the LU Decomposition of a matrix.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1.Define the package as scipy.linalg import lu.</br>
2.Get input from user and print L and U matrix by 'print'.</br>
3.Define a package as "from scipy.linalg import lu_factor, lu_solve" and create the variable as 'X' include the package in that variable.</br>
4.print the variable 'X' </br>

## Program:
(i) To find the L and U matrix
```
'''Program to find L and U matrix using LU decomposition.
Developed by: RUDESH KANNA R
RegisterNumber: 24900303
'''
import numpy as np
from scipy.linalg import lu
A=np.array(eval(input()))
P,L,U=lu(A)
print(L)
print(U)Define the package as scipy.linalg import lu.
Get input from user and print L and U matrix by 'print'.
Define a package as "from scipy.linalg import lu_factor, lu_solve" and create the variable as 'X' include the package in that variable.
print the variable 'X'
```
(ii) To find the LU Decomposition of a matrix
```
'''Program to solve a matrix using LU decomposition.
Developed by: RUDESH KANNA R
RegisterNumber: 24900303
'''

# To print X matrix (solution to the equations)


import numpy as np

def lu_decomposition(A):
    n = A.shape[0]
    L = np.zeros((n, n))
    U = A.copy()
    
    for i in range(n):
        L[i, i] = 1  
        for j in range(i + 1, n):
            factor = U[j, i] / U[i, i]
            L[j, i] = factor
            U[j, :] -= factor * U[i, :]
    
    return L, U

def forward_substitution(L, b):
    n = L.shape[0]
    y = np.zeros(n)
    
    for i in range(n):
        y[i] = b[i] - np.dot(L[i, :i], y[:i])
    
    return y

def backward_substitution(U, y):
    n = U.shape[0]
    x = np.zeros(n)
    
    for i in range(n - 1, -1, -1):
        x[i] = (y[i] - np.dot(U[i, i + 1:], x[i + 1:])) / U[i, i]
    
    return x

A = np.array([[3, 2, 7], 
              [2, 3, 1], 
              [3, 4, 1]], dtype=float)

b = np.array([4, 5, 7], dtype=float)

L, U = lu_decomposition(A)

y = forward_substitution(L, b)

x = backward_substitution(U, y)

print(x)
```

## Output:
![image](https://github.com/user-attachments/assets/c48125a0-ed08-42d7-a454-50fbb927dfcb)


![image](https://github.com/user-attachments/assets/8e9cb1bd-f9c6-4adc-9211-8fbbbaea03d4)



## Result:
Thus the program to find the LU Decomposition of a matrix is written and verified using python programming.

