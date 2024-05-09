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

Failure Inducing Input: 
```
  @Test 
  public void testReversed2() { 
    int[] input2 = {2,3,4,5,6,7}
    assertArrayEquals(new int[]{7,6,5,4,3,2}, ArrayExamples.reversed(input2)); 
  } 
```

Non Failure Inducing Input: 
```
  @Test
    public void testReversed() {
      int[] input1 = { };
      assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
 Symptoms For testReversed2() and testReversed(): 
![image](https://github.com/XiaoFengLin123/cse15l-lab-report3/assets/146484956/742d3d93-1052-40b0-bc49-6029197561cb)

Old with buggy code: 
``` 
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

New with fixed code:

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

The fixed code address the issues with the old code by filling in the `newArray` with elements from the original array `arr` itself. By using changing `newArrya[i] = arr[arr.length - i - i]` from `arr[i] = newArray[arr.length - i - 1]`. We are able to get the elements from the original array in a reverse order and put them into the new array. It ensures that elements from the end of `arr` is placed corresponding to the start of the `newArray`. The changed code also outputs the new array `newArray` with the reversed elements instead of the original array `arr` which allowed the `testReversed()` to pass since it just outputs an empty array since it doesn't need to reverse the elements within an empty array. 
