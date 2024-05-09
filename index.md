**Part 1**

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

**Part 2**

Source for line commands for `grep`: https://www.golinuxcloud.com/grep-command-in-linux/#google_vignette

`grep -i pattern file_name`

First Example: `grep -i desktop biomed/*.txt` 

Output: 

```
biomed/1471-2105-4-28.txt:        BPNN, on the other hand, adesktop computer is the only
biomed/1471-2202-3-1.txt:          disk of a desktop computer. The output is a direct plot
biomed/1471-2474-4-8.txt:            desktop μCT system (μCT 20, Scanco Medical AG,
biomed/1472-6947-2-7.txt:          will increasingly allow extension of desktop systems and
biomed/1475-925X-2-10.txt:          desktop PC. The regions studied were the central
biomed/gb-2001-2-2-research0004.txt:        polystyrene using a desktop jet printer [ 19] and onto
biomed/gb-2002-3-7-research0037.txt:          written in FORTRAN and run on desktop PCs [ 13].
biomed/gb-2003-4-6-r41.txt:        a desktop computer. To make this methodology better suited
```

Second Example`grep -i pH biomed/1471-2091-3-17.txt`

Output: 
```
relevant to understanding the pathophysiology of jaundice
        solubility (S) at any pH is determined by S
          values, and pH [ 2 ] :
        measurements of buffer pH and of the pK
        and require that solutions are below saturation at all pH
        aqueous UCB is acidified to neutral or low pH's, "Usually a
          of most samples below pH 7.2. Overall recoveries (UCB in
          at pH 5.86 to 166 μM at pH 8.38. At N = 0.086 (Fig. 1B),
          [UCB] ranged from 0.3 to 2.4 μM at pH 4.50 and from 1.4
          to 6.4 μM at pH 7.05 and most of the UCB sedimented. By
          contrast, at pH 7.56 and 7.70 (phosphate), only minor
          ranged from 0.1 to 2.7 μM at all three pH values (4.15 to
          new solid phase [ 19 20 ] . Our centrifugation, 5 min at
          To evaluate the important effect of pH on
          any pH, e.g. 62 nM at pH 7.4 and 0.32 μM at pH 8.5, can
          g  for a few hours, was 100 nM at pH
          lowest [UCB] increased rapidly with increasing pH, to 17
          μM (150 times S) at pH 8.05 and 34 μM (230 times S) at pH
          ] . In contrast, below pH 6.7, sedimentation of 10 μM UCB
          dearth of stabilizing UCB anions at this pH, as expected
          increasing pH (Fig. 1A,1B,1C). At each N
          lowest pH values: 0.1 μM (N = 0.025, pH 4.15); 0.3 μM (N
          = 0.086, pH 4.5); and 2.8 &#956;M (N = 0.31, pH 5.9).
          example, data from 1-naphthoic acid in DMSO-water [ 22 ]
          explains in part the relatively high [UCB] at high pH at
          The pH effects on [UCB] at each N
          [UCB] at each pH registered relatively small increases
          with significant increases in pH: for example from 0.1 μM
          (pH 4.14) to 0.2 μM (pH 7.0) at N = 0.025; from 0.3 μM
          (pH 4.5) to 1.4 μM (pH 7.1) at N = 0.086; and from 111 μM
          (pH 7.1) to 166 μM (pH 8.4) at N = 0.31. These increases
          true solubility (S) at the high pH (Eq. 1), the required
          sedimentation from phosphate buffers at pH 7.6-7.7, as
          compared to Tris buffer at pH 7.1, can be ascribed mainly
          to the much higher pH values and ionic strength of the
          phosphate systems. Another significant factor may be the
          difference in charge between the buffer salts; phosphate
          the relevant physical properties of UCB and MBR, and of
          thus more hydrophobic and should be less soluble in water
          compared to our lowest [UCB] of 0.3 μM at pH 4.5 and 1.4
          μM at pH 7.05. At this N, 9 of 11 MBR data points were
          obtained at pH below 7.05 and 5 below pH 4.5 [ 4 ] , so
          = 0.31, our lowest [UCB], 2.8 μM at pH 5.9, was close to
          4 5 ] . Thus, many data points, obtained at pH values
          phase [ 2 ] . For example, at pH 8.5 and a UCB
          previously that inaccuracies in the pH measurements
          inaccuracies in pH measurement produced serious errors in
          Many methods, using appropriate pH measurements, have
          justified, to assume that pH values do not change on
          adding DMSO [ 3 4 5 6 7 ] , or to use uncalibrated pH
            values, along with the experimental S values at pH
        fairly high pH values, are low at DMSO mole fractions up to
        determination of [H +] or pH. Unless pK
          values and the pH. The 13C-NMR data, suggesting low pK
        did not meet these essential requirements of proper pH
        to the effects of pH on the precipitation of calcium
          Stock buffers, 1.0 M, were: Tris-HCl, pH 7.01; Na-
          phosphate, pH 6.85, or 6.99; and Na-acetate, pH 4.01.
          0.1 M Tris-HCl buffer, pH 7.01, were prepared freshly for
          coefficient, ε, 47,000 M -1.cm -1 [ 18 ] . The pH
          4  [ 8 ] . The 0.1 M phosphate buffer
          spectrophotometrically within 20 min. The precipitates
          in DMSO for spectrophotometry. Absorbance (
          in 0.1 M Tris-HCl buffer, pH 7.01. Microcentrifugation
        a given pH; S
```

`grep -w pattern file_name`

`grep -r pattern *`

`grep -v pattern file_name`

