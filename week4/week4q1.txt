#include<iostream>
using namespace std;
int count=0;
int merge(int arr[],int mid,int l,int r){
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
    int i=0;
    int j=0;
    int k=l;
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
        count++;
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
    return count;
}
int  mergesort(int arr[],int l,int r){
    int inversion=0;
    if(l<r){
        int mid=(l+r)/2;
        inversion+=mergesort(arr,l,mid);
        inversion+=mergesort(arr,mid+1,r);
        inversion+=merge(arr,mid,l,r);
    }
    return inversion;
}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        int arr[n];
        for(int i=0;i<n;i++){
            cin>>arr[i];
        }
        int inv=mergesort(arr,0,n-1);
        for(int i=0;i<n;i++){
            cout<<arr[i]<<" ";
        }
        cout<<"comparision"<<count;
        cout<<"inversion"<<inv<<endl;
        count=0;
    }
    return 0;
}