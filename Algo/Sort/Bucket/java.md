### Code:

```
public void bucketsort(int[] input) {
  final int[] code = hash(input);
  
  List<Integer>[] buckets = new List[code[1]];
  
  for (int i = 0; i < code[1]; i++) {
    buckets[i] = new ArrayList<Integer>();
  }
  
  for (int i : input) {
    buckets[hash(i, code)].add(i);
  }
 
  for (List bucket : buckets) {
    Collections.sort(bucket);
  }
  
  int ndx = 0;
  for (int b = 0; b < buckets.length; b++) {
    for (int v : buckets[b]) {
      input[ndx++] = v;
    }
  }
}
 
private int[] hash(int[] input) {
  int m = input[0];
  for (int i = 1; i < input.length; i++) {
    if (m < input[i]) {
      m = input[i];
    }
  }
  return new int[]{m, (int) Math.sqrt(input.length)};
}
 
private int hash(int i, int[] code) {
  return (int) ((double) i / code[0] * (code[1] - 1));
}
```

### Ref:
https://github.com/pooyahatami/Algorithm-Sort-Bucket
