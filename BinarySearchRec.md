# Binary Search Using Recursion
Note : variables`s` and `e` are declared in the main function
```java
static int binarySearch(int[] arr,int target, int s, int e){
        if (s>e){
            return -1;
        }
        int m = s + (e-s)/2;
        if(target == arr[m]){
            return m;
        }

        if(target < arr[m]){
            return binarySearch(arr,target,s,m-1);
        }
        return binarySearch(arr,target,m+1,e);
    }
```
