# Sorting Algorithm
## Bubble sort
```
public static void bubbleSort(int[] arr) {  
    for (int i = 0; i < arr.length - 1; i++) {  
        for (int j = 0; j < arr.length - i - 1; j++) {  
            if (arr[j] > arr[j + 1]) {  
                int temp = arr[j];  
                arr[j] = arr[j + 1];  
                arr[j + 1] = temp;  
            }  
        }  
    }  
}

// optimized bubble sort
public void bubbleSort(int[] arr) {  
    for (int i = 0; i < arr.length - 1; i++) {  
        boolean isSorted = true;  
        for (int j = 0; j < arr.length - i - 1; j++) {  
            if (arr[j] > arr[j + 1]) {  
                isSorted = false;  
                int temp = arr[j];  
                arr[j] = arr[j + 1];  
                arr[j + 1] = temp;  
            }  
        }  
        if (isSorted) {  
            break;  
        }  
    }  
}
```
## Selection sort
```
public void selectionSort(int[] arr) {  
    for (int i = 0; i < arr.length - 1; i++) {  
        int minIndex = i;  
        for (int j = i + 1; j < arr.length; j++) {  
            if (arr[j] < arr[minIndex]) {  
                minIndex = j;  
            }  
        }  
        if (minIndex != i) {  
            int temp = arr[i];  
            arr[i] = arr[minIndex];  
            arr[minIndex] = temp;  
        }  
    }  
}
```
## Insertion Sort
```
public void insertionSort(int[] arr) {  
    for (int i = 1; i < arr.length; i++) {  
        int insertIndex = i;  
        int insertValue = arr[i];  
  
        while (insertIndex > 0 && insertValue < arr[insertIndex - 1]) {  
            arr[insertIndex] = arr[insertIndex - 1];  
            insertIndex--;  
        }  
  
        arr[insertIndex] = insertValue;  
    }  
}
```
## Shell sort
```
public void shellSort(int[] arr) {  
    for (int gap = arr.length / 2; gap > 0; gap /= 2) {  
        for (int i = gap; i < arr.length; i++) {  
            int insertIndex = i;  
            int insertValue = arr[i];  
  
            while (insertIndex - gap >= 0 
		            && insertValue < arr[insertIndex - gap]) {  
                arr[insertIndex] = arr[insertIndex - gap];  
                insertIndex -= gap;  
            }  
  
            arr[insertIndex] = insertValue;  
        }  
    }  
}
```
## Quick sort
```
public void quickSort(int[] arr, int low, int high) {  
    if (low < high) {  
        int pos = partition(arr, low, high);  
        quickSort(arr, low, pos - 1);  
        quickSort(arr, pos + 1, high);  
    }  
}  
  
public int partition(int[] arr, int low, int high) {  
    int pivot = arr[high];  
  
    while (low < high) {  
        while (low < high && arr[low] <= pivot) {  
            low++;  
        }  
        arr[high] = arr[low];  
  
        while (low < high && arr[high] >= pivot) {  
            high--;  
        }  
        arr[low] = arr[high];  
    }  
    arr[low] = pivot;  
    return low;  
}
```
## Merge sort
```
 public void mergeSort(int[] arr, int left, int right){  
    if(left < right){  
        int mid = (left + right) / 2;  
        mergeSort(arr, left, mid);  
        mergeSort(arr, mid + 1, right);  
        merge(arr, left, mid, right);  
    }  
}  
  
public void merge(int[] arr, int left, int mid, int right){  
    int[] tempArr = new int[arr.length];  
    int i = left, j = mid + 1, t = 0;  
  
  
    while(i <= mid && j <= right){  
        if(arr[i] < arr[j]){  
            tempArr[t] = arr[i];  
            i++;  
            t++;  
        } else {  
            tempArr[t] = arr[j];  
            j++;  
            t++;  
        }  
    }  
  
    while(i <= mid){  
        tempArr[t] = arr[i];  
        i++;  
        t++;  
    }  
  
    while(j <= right){  
        tempArr[t] = arr[j];  
        j++;  
        t++;  
    }  
  
    int k = left;  
    t = 0;  
    while(k <= right){  
        arr[k] = tempArr[t];  
        k++;  
        t++;  
    }  
}  
  
public int[] sortArray(int[] nums) {  
    mergeSort(nums, 0, nums.length - 1);  
    return nums;  
}
```
## Heap sort
```
public void heapSort(int[] arr) {  
    // construct a max heap  
    for (int i = arr.length / 2 - 1; i >= 0; i--) {  
        heapify(arr, arr.length, i);  
    }  
  
    // sort  
    for (int i = arr.length - 1; i > 0; i--) {  
        int temp = arr[0];  
        arr[0] = arr[i];  
        arr[i] = temp;  
        heapify(arr, i, 0);  
    }  
}  
  
public void heapify(int[] arr, int length, int i) {  
    int largest = i;  
    int left = i * 2 + 1;  
    int right = i * 2 + 2;  
  
    if (left < length && arr[largest] < arr[left]) {  
        largest = left;  
    }  
  
    if (right < length && arr[largest] < arr[right]) {  
        largest = right;  
    }  
  
    if (largest != i) {  
        int temp = arr[i];  
        arr[i] = arr[largest];  
        arr[largest] = temp;  
        heapify(arr, length, largest);  
    }  
}
```