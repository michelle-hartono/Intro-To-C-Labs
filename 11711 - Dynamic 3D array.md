# 11711 - Dynamic 3D array

## Brief
Design two functions:
```
unsigned*** new_3d_array(unsigned n,unsigned m,unsigned k);
void delete_3d_array(unsigned ***arr);
```
## Solution
```c=

#ifndef FUNCTION_H_INCLUDED
#define FUNCTION_H_INCLUDED
#include <stdlib.h>
#include <stdio.h>
unsigned*** new_3d_array(unsigned n,unsigned m,unsigned k);
void delete_3d_array(unsigned ***arr);
unsigned*** new_3d_array(unsigned n,unsigned m,unsigned k){
    unsigned ***ptr1,**ptr2,*ptr3;
    ptr1=(unsigned ***)malloc(n*sizeof(unsigned**)+n*m*sizeof(unsigned*)+n*m*k*sizeof(unsigned));
    
    ptr2 = (unsigned**)(ptr1+n);
    for(int i=0;i<n;i++,ptr2+=m){
        *(ptr1+i)=ptr2;
    }
    
    ptr3 = (unsigned*)ptr2;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++,ptr3+=k){
            *(*(ptr1+i)+j)=ptr3;
        }
    }
    return ptr1;
}
void delete_3d_array(unsigned ***arr){
    free(arr);
}
#endif // FUNCTION_H_INCLUDED

```