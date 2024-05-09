The bug we'll be using is within the reversed method, which returns a new array with all of the elements of the input array in reverse order. 

The Buggy program: 
``` 
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
