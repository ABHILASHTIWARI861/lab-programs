## Warshal algorithm
### code
```c
#include<stdio.h>
#include<stdlib.h>
int i,j,k,p[10][10],a[10][10],n;
void path(){
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            p[i][j]=a[i][j];
        }
    }
    for(int k=0;k<n;k++){
        for(int i=0;i<n;i++)
        for(int j=0;j<n;j++){
            if(p[i][k]==1 && p[k][j]==1){
                p[i][j]=1;
            }
        }
    }
}
int main(){
    printf("enter the no of node");
    scanf("%d",&n);
    printf("enter Adjancy matrix");
    for(int i=0;i<n;i++){
        for(int j=0;j<n;j++){
            scanf("%d",&a[i][j]);
        }
    }
    path();
    printf("path matrix\n");{
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                printf("%d",p[i][j]);
            }
             printf("\n");
        }
    }
}

output
enter the no of node4
enter Adjancy matrix
0 1 0 0 
0 0 1 0
0 0 0 1
0 0 0 0 
path matrix
0111
0011
0001
0000