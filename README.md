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

import numpy as np

def QR_Decomposition(A):
    
    n,m=A.shape
    
    Q=np.empty((n,n))
    
    u=np.empty((n,n))
    
    u[:,0]=A[:,0]
    
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    
    for i in range(1,n):
    
        u[:,i]=A[:,i]
        
        for j in range(i):
        
            u[:,i]-=(A[:,i]@Q[:,j])*Q[:,j]
            
            Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
    
    R=np.zeros((n,m))
    
    for  i in  range (n):
    
        for j in range (i,m):
        
            R[i,j]=A[:,j]@Q[:,i]
    
    print(Q)
    
    print(R)

a = np.array(eval(input()))

QR_Decomposition(a)

### Gram-Schmidt Method
```
The Gram-Schmidt Method is a process for orthonormalizing a set of vectors in an inner product space. Here's a step-by-step guide:

Step 1: Start with a set of linearly independent vectors
Begin with a set of vectors {v1, v2, ..., vn} that are linearly independent.

Step 2: Normalize the first vector
Normalize the first vector v1 by dividing it by its magnitude (length). This gives the first orthonormal vector u1.

Step 3: Find the second orthonormal vector
Calculate the projection of v2 onto u1, then subtract this projection from v2. Normalize the resulting vector to obtain the second orthonormal vector u2.

Step 4: Repeat the process for remaining vectors
Continue this process for each remaining vector vi, calculating its projection onto the previously determined orthonormal vectors u1, u2, ..., ui-1, subtracting these projections, and normalizing the result to obtain the next orthonormal vector ui.

The final set of orthonormal vectors {u1, u2, ..., un} is the result of the Gram-Schmidt process.

Example Use Case
Suppose we have two vectors v1 = [3, 4] and v2 = [1, 2] in ℝ². We can apply the Gram-Schmidt process to obtain an orthonormal basis.

First, normalize v1:

u1 = v1 / ||v1|| = [3/5, 4/5]

Next, calculate the projection of v2 onto u1:

proj_v2_u1 = (v2 · u1) * u1 = [9/25, 12/25]

Subtract this projection from v2:

v2_perp = v2 - proj_v2_u1 = [-4/25, -8/25]

Normalize v2_perp:

u2 = v2_perp / ||v2_perp|| = [-2/√5, -4/√5]

The resulting orthonormal basis is {u1, u2}.

```

## Output
![Screenshot 2024-12-02 085455](https://github.com/user-attachments/assets/38022637-a642-43bc-baea-0621afa63c44)




## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
