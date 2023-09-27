# Key Concepts

## Special matrices

### Diagonal matrices
*   Have only nonzero entries on the diagonal 
*   Can be rectangular
*   Scales space
*   Inverse is diagonal matrix with inverse entries

### Orthogonal matrices
*  Square matrix where every column is a unit vector and every pair of columns is orthogonal
*  Rotates space
*  Its inverse is its transpose

### Symmetric matrices
*  Square matrix where $a_{ij} = a_{ji}$
*  Equals its own transpose
*  Eigenvalues are always real (not complex)
*  Eigenvectors associated with different eigenvalues are orthogonal

## Matrix decomposition

* Factorization of a matrix into a product of matrices 
* Product matrices might be more compact/ordered, could make computations easier, could shed light on matrix structure

### Eigendecomposition
*  $A = VDV^{-1}$ where V has eigenvectors as columns and D is diagonal matrix with eigenvalues on the diagonal
*  Can only do this if A is square and if eigenvectors of A form a basis for space
*  $A^n = VD^nV^{-1}$
*  $A^{-1} = VD^{-1}V^{-1}$

### Singular value decomposition
*  `np.linalg.svd`
*  $A = USV^T$ where U/V are orthogonal matrices and S is diagonal
*  Can decompose any matrix this way
*  Diagonal entries of S are singular values, columns of U are left singular values, columns of V are right singular values
* Decomposes transformation that matrix enacts into a rotation, then a scaling, then a rotation
* Columns of V associated with zero or non-existant singular values form an orthogonal basis for the nullspace of A
* Columns of U associated with non-zero singular values form an orthogonal basis for the column space of A
* rank(A) = number of non-zero singular values
* SVD factorizes A into sum of outer products with decreasing influence, can use first K sums to form rank K approximation of A

## Dimensionality Reduction
* Transform data from high D to low D while keeping as much information as possible about the data (finding new representation for the data)
* Can help with data visualization, noise reduction, data preprocessing for further analyses, and scientific findings, among other things

### Principal components analysis
* `sklearn.decomposition.pca` for PCA, see info at the end of this tutorial
*  Find axes in space that maximize the variance of the data (and minimize the residuals) while being orthongal to each other. Project data onto these axes and keep first K components
* Can think of PCA as a change of basis where the new basis vectors are the principal components
* $U = XV$ where U is the transformed data (# data points x reduced dim), X is the data matrix (# data points x orig dim), and V is the components matrix (orig dim x reduced dim)
* Always center your data first!
* Can find principal components as the eigenvectors of the covariance matrix ($\frac{1}{n}X^TX$), eigenvalues tell you the variance explained by that component (plot these to make a scree plot) 
* Could also use SVD to find PCA - the columns of V are the eigenvectors of the covariance matrix and the squared singular values over N are the eigenvalues
