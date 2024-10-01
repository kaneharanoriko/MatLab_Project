Singular Value Decomposition
Low Rank Matrix Approximation
If a matrix  has rank , then we can write

If  and  has rank larger than , then the euality above no longer holds. However, if  is small, then it is almost true. Hence, the SVD is a useful way to find low rank approximation of matrices.

Let's try out an example. Let's read in an image and store this as a matrix A.
% Read in an image
IMG = imread( 'cameraman.tif' );    

% If it is a color image, we will only retain one of the color channels
A = double( IMG( :,:,1 ) );     

% Display image
imshow( uint8( A ) )        

% Size of the image
size( A )

Note that if were to store or transmit this image/matrix, we will need to store/transmit  numbers. Instead, we can compute a low rank approximation to the matrix  using the SVD.
% Compute the SVD of A
[ U, Sigma, V ] = svd( A );

% Let's compute a low rank approximation
r = 10; 
B = U( :, 1:r ) * Sigma( 1:r,1:r ) * V( :, 1:r )';   

% Display the low-rank approximation as an image
imshow( uint8(B) );

Try changing the value of r above and record your observations. Note that if we were to transmit the low matrix/image corresponding to the low rank approximations, we only need to transmit  corresponding to . This corresponds to  numbers which can be much smaller than  for small .
