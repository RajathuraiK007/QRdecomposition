# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Rajathurai K
RegisterNumber: 212225100036
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
def QR_Decomposition(A):
    m,n=A.shape
    
    Q=np.empty((m,n))
    u=np.empty((m,n))
    
    u[:,0]=A[:,0]
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,n):
        u[:,i]=A[:,i]
        for j in range(i):
            u[:,i]-=(np.dot(A[:,i],Q[:,j])*Q[:,j])
        Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    R=np.zeros((n,n))
    for i in range(n):
        for j in range(i,m):
            R[i,j]=A[:,j]@Q[:,i]
    print("The Q Matrix is \n",Q)
    print("The R Matrix is \n",R)
a = np.array(eval(input()))
QR_Decomposition(a)






```

## Output:

<img width="1476" height="854" alt="image" src="https://github.com/user-attachments/assets/62f2dfc4-b10c-4da1-8379-2362e0065d3b" />

<img width="1467" height="758" alt="image" src="https://github.com/user-attachments/assets/3b525d1e-33ea-4829-ba70-42a58007d2d8" />


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
