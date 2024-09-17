# MargeSort
This is a sorting algorithm
#include<iostream>
using namespace std;

void margeSort(int arr[], int start, int end);
void marge(int arr[], int start, int mid, int end);
void printArray(int arr[], int length);

int main() {

    int length = -1;
    while(length<=-1) {
        cout<<"Enter array length : ";
        cin>>length;
    }

    int arr[length];

    for(int i=0; i<length; i++) {
        cout<<"Enter "<<i+1<<" element : ";
        cin>>arr[i];
    }

    cout<<"Unsorted array : ";
    printArray(arr, length);

    margeSort(arr, 0, length-1);

    cout<<"Sorted array : ";
    printArray(arr, length);

    return 0;
}

void margeSort(int arr[], int start, int end) {

    if(end>start) {

        int mid = (end+start)/2;

        margeSort(arr, start, mid);
        margeSort(arr, mid+1, end);

        marge(arr, start, mid, end);
    }
}

void marge(int arr[], int start, int mid, int end) {

    int leftLen = mid - start + 1;
    int rightLen = end - mid;

    int arrayLeft[leftLen], arrayRight[rightLen];

    for(int i=0; i<leftLen; i++) {
        arrayLeft[i] = arr[start + i];
    }

    for(int i=0; i<rightLen; i++) {
        arrayRight[i] = arr[mid + i + 1];
    }

    int i, j, k;
    i = j = 0;
    k = start;

    while(i<leftLen && j<rightLen) {

        if(arrayLeft[i]<=arrayRight[j]) {
            arr[k] = arrayLeft[i];
            i++;
        } else {
            arr[k] = arrayRight[j];
            j++;
        }
        k++;
    }

    while(i<leftLen) {

        arr[k] = arrayLeft[i];
        i++;
        k++;
    }

    while(j<rightLen) {

        arr[k] = arrayRight[j];
        j++;
        k++;
    }
}

void printArray(int arr[], int length) {

    for(int i=0; i<length; i++) {
        cout<<arr[i]<<" ";
    }

    cout<<endl;
}
