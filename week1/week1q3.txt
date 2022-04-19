#include <stdio.h>
#include <stdlib.h>
#define MAX 50
int count;
int jumpsearch(int[],int ,int );
int main(){
    int a[MAX],n,x,t=0,k;
    scanf("%d",&t);
    for(int i=0; i<t; i++){
        count=0;
        scanf("%d",&n);
        for(int i=0; i<n; i++)
            scanf("%d",&a[i]);
        scanf("%d",&k);
        x=jumpsearch(a,n-1,k);
    if(x==k)
        printf("Present %d\n",count);
    else
        printf("Not Present %d\n",count);
    }
    return 0;
}

int jumpsearch(int a[],int n,int k){
    int st=0,end=2;
    while(a[end]<k&&end<n) {
        count++;
        st=end;
        end+=2;
    }
    printf("%d",count);
    if(end>n)
        end=n;
        printf("%d",end);
    for(int i=st;i<=end;i++){
        count++;
        if(a[i]==k) {
            return a[i];
        }
    }
    return -1;}