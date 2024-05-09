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


