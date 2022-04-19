#include<iostream>
using namespace std;
void merge(int arr[],int l,int mid,int r){
    int n1=mid-l+1;
    int n2=r-mid;
    int a[n1];
    int b[n2];
    for(int i=0;i<n1;i++){
        a[i]=arr[l+i];
    }
    for(int i=0;i<n2;i++){
        b[i]=arr[mid+1+i];
    }
    int i=0,j=0,k=l;
    while(i<n1 && j<n2){
        if(a[i]<b[j]){
            arr[k]=a[i];
            k++;
            i++;
        }
        else{
            arr[k]=b[j];
            k++;
            j++;
        }
    }
    while(i<n1){
        arr[k]=a[i];
            k++;
            i++;
    }
    while(j<n2){
         arr[k]=b[j];
            k++;
            j++;
    }
}
void mergesort(int arr[],int l,int r){
    if(l<r){
        int mid=(l+r)/2;
        mergesort(arr,l,mid);
        mergesort(arr,mid+1,r);
        merge(arr,l,mid,r);
    }
}
void findduplicate(int arr[],int i,int j,int key){
    int flag=0;
    while(i<j){
        if(arr[i]+arr[j]==key){
            flag=1;
            cout<<arr[i]<<" "<<arr[j]<<endl;
            i++;j--;
        }
        else if(arr[i]+arr[j]<key){
            i++;
        }
        else{
            j--;
        }
    }
    if(flag=0){
        cout<<"No such element exist"<<endl;
    }
}
int main(){
    int t;
    cin>>t;
    for(int i=0;i<t;i++){
        int n;
        cin>>n;
        int arr[n];
        for(int i=0;i<n;i++){
            cin>>arr[i];
        }
        int key;
        cin>>key;
        mergesort(arr,0,n-1);
        findduplicate(arr,0,n-1,key);
    }
    return 0;
}