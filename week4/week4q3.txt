#include<iostream>
using namespace std;
void countsort(int arr[],int n){
    int mx=0;
    for(int i=0;i<n;i++){
        mx=max(mx,arr[i]);
    }
    int count[mx+1]={0};
    for(int i=0;i<n;i++){
        count[arr[i]]++;
    }
    for(int i=1;i<=mx;i++){
        count[i]+=count[i-1];
    }
    int output[n];
    for(int i=n-1;i>=0;i--){
        output[--count[arr[i]]]=arr[i];
    }
    for(int i=0;i<n;i++){
        arr[i]=output[i];
    }
}
int main(){
    int n;
    cin>>n;
    int arr[n];
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    countsort(arr,n);
    int k;
    cin>>k;
    cout<<arr[k-1]<<endl;
    cout<<arr[n-k]<<endl;
    return 0;
}