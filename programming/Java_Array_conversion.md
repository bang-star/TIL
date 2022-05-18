# Java Array_Conversion

## 1. int Array → String

<br />

``` Java
    int[] arr = {1,2,3,4};
    String str = Arrays.toString(arr);
```

## 2. int Array → Integer Array
<br />

``` Java
    int[] arr = {1,2,3,4};
    Integer[] arr2 = Arrays.stream(arr).boxed().toArray(Integer[]:new);
```

## 3. Integer Array → int Array
<br />

``` Java
    Integer[] arr = {1,2,3,4};
    Int[] arr2 = Arrays.stream(arr).mapToInt(Integer::intValue).toArray();
```

## 4. int Array → Integer List
``` Java 
    int[] arr = {1,2,3};
    List<Integer> list = Arrays.stream(arr).boxed().collect(Collectors.toList());
```

## 5. int Array → Integer ArrayList 
``` Java
     int[] arr = {10, 20, 30, 40};
    ArrayList<Integer> integerArray = (ArrayList<Integer>) Arrays.stream(arr).boxed().collect(Collectors.toList());
```

### 6. Integer List → int Array OR Integer ArrayList → int Array
``` Java
    List<Integer> list =  new ArrayList<Integer>();
    int[] arr = list.stream().mapToInt(i -> i).toArray();
```

<br />
<hr />
<br />

## Comment
    - 알고리즘 풀이시 자주 사용하지만, 자주 까먹는 메소드


<br />
<hr />
<br />

## 참고
1. [DelftStack](https://www.delftstack.com/howto/java/arraylist-to-int-array-in-java/)