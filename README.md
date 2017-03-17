#About these classes:

###CRS.h

* This file contains class to store a sparse matrix in Compressed Row Storage format
* It can also be used independently to store any sparse matrix in CRS format
* Creating objects: ```CRS<data-type-of-elements> obj-name(input-matrix, flag)```
* Input matrix: A 2-D vector. ```vector<vector<data-type> >```
* ```flag``` = 0, if you want to delete the input matrix after storing in CRS format. (Recommended for large Matrices)
			 = 1, if you don't want to delete input matrix
* Currently Methods available includes just Matrix-Vector multiplication. Usage:
			```C=A.MVMult(B); // performs c=A.b```
				where,
					A=CRS object created with the input matrix
					B=Vector to be multiplied
					C=Result Vector
	I'll add more methods when I find some free time.

###CGCRYLOV.h

* This file contains class to solve AX=B system
* Creating objects: ```CGCRYLOV<data-type-of-elements>=obj-name(problem-size)```
* Requires CRS.h to be in the same folder
* Require CBLAS
* Methods available:
	* ``` X=Solve(A,B) ```

		Where,
			A=2D vector ```vector<vector<data-type> >```
			B=1D vector
			X=Result vector
		This method solves any AX=B for positive definite A matrix.

	* ``` X=SolvePreCond(A,M,B) ```

		Where,
			A=2D vector ```vector<vector<data-type> >```
			M=2D vector ```vector<vector<data-type> >```
			B=1D vector
			X=Result vector
		This method solves any AX=B for positive definite A matrix with preconditioner M.

	* ``` X=SolveCRS(A,M,B) ```

		Where,
			A=CRS Object created with input sparse matrix
			B=1D vector
			X=Result vector
		This method solves any AX=B for positive definite sparse A matrix.

	* ``` X=SolvePreCondCRS(A,M,B) ```

		Where,
			A=CRS Object created with input sparse matrix
			M=CRS Object created with input preconditioner
			B=1D vector
			X=Result vector
		This method solves any AX=B for positive definite sparse A matrix with preconditioner M.