# halfband

Based directly on http://www.musicdsp.org/showone.php?id=39

## Compiling
No dependencies, so just:

    gcc halfband.c -c -Wall
    
Compile and run the test code:

    gcc -Wall halfband.c test_halfband.c -o test_halfband 
    
    
## Usage example

Create a cascade for 8x oversampling:
    
    // 8=2^3, 10=order of filter, 0=not steep filter
    cascade = create_half_cascade(3, 10, 0);
    
Apply the filter to an array, 8 samples at a time:

    // assuming you have double *in, double *out, with n samples in
    for(i=0;i<n;i+=8)
        out[i>>3] = process_half_cascade(cascade, &(in[k]));
        
        
        