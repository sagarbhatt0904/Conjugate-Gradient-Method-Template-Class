# About these classes:

### CRS.h

* This file contains class to store a sparse matrix in Compressed Row Storage format
* It can also be used independently to store any sparse matrix in CRS format
* Creating objects: ```CRS<data-type-of-elements> obj-name(input-matrix, flag)```
* Input matrix: A 2-D vector. ```vector<vector<data-type> >```
* ```flag``` = 0, if you want to delete the input matrix after storing in CRS format. (Recommended for large Matrices) <br />
			 = 1, if you don't want to delete input matrix
* Currently Methods available includes just Matrix-Vector multiplication. Usage:
			```C=A.MVMult(B); // performs c=A.b```
				where,
					A=CRS object created with the input matrix <br />
					B=Vector to be multiplied <br />
					C=Result Vector <br />
	
### CGCRYLOV.h

* This file contains class to solve AX=B system
* Creating objects: ```CGCRYLOV<data-type-of-elements>=obj-name(problem-size)```
* Requires CRS.h to be in the same folder
* Require CBLAS
* Methods available:
	* ``` X=Solve(A,B) ```

		Where, <br />
			A=2D vector ```vector<vector<data-type> >``` <br />
			B=1D vector <br />
			X=Result vector <br />
		This method solves any AX=B for positive definite A matrix. 

	* ``` X=SolvePreCond(A,M,B) ```

		Where, <br />
			A=2D vector ```vector<vector<data-type> >``` <br />
			M=2D vector ```vector<vector<data-type> >``` <br />
			B=1D vector <br />
			X=Result vector <br />
		This method solves any AX=B for positive definite A matrix with preconditioner M.

	* ``` X=SolveCRS(A,M,B) ``` 

		Where, <br />
			A=2D vector ```vector<vector<data-type> >``` <br />
			B=1D vector <br />
			X=Result vector <br />
		This method solves any AX=B for positive definite sparse A matrix.

	* ``` X=SolvePreCondCRS(A,M,B) ```

		Where, <br />
			A=2D vector ```vector<vector<data-type> >``` <br />
			M=2D vector ```vector<vector<data-type> >``` <br />
			B=1D vector <br />
			X=Result vector <br />
		This method solves any AX=B for positive definite sparse A matrix with preconditioner M.
