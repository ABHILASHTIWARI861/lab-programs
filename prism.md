# prism Algorithm
## code
````c
#include<stdio.h>
#include<stdlib.h>
int i,j,k,a,b,u,v,n,ne=1;
int cost[10][10],min_cost=0,visited[10]={0},min;
int main(){
    printf("enter number of nodes");
    scanf("%d",&n);
    printf("enter adjancy matrix");
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            scanf("%d",&cost[i][j]);
            if(cost[i][j]==0){
                cost[i][j]=999;
            }
        }
    }
    visited[1]=1;
    printf("\n");
    while(ne<n){
        min=999;
        for(int i=1;i<=n;i++){
            for(int j=1;j<=n;j++){
                if(cost[i][j]<min){
                    if(visited[i]!=0){
                    min=cost[i][j];
                    a=u=i;
                    b=v=j;
                }
                }
            }
        }
        if(visited[u]==0 || visited[v]==0){
            printf("\n %d edges(%d--->>%d):%d",ne++,a,b,min);
            min_cost=min_cost+min;
            visited[b]=1;
        }
        cost[a][b]=cost[b][a]=999;
    }
    printf("cost of minimum spaning tree %d",min_cost);
    return 0;
}

### output
enter number of nodes4
enter adjancy matrix
0 10 20 50
20 0 60 999
10 60 0 40
50 999 0 40


 1 edges(1--->>2):10
 2 edges(1--->>3):20
 3 edges(3--->>4):40cost of minimum spaning tree 70
