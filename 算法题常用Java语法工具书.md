# 继承

`Vector` <- `Stack`, `Collection`

`Collection` <- `List`, `Set`

# 初始化 Initialize

## `Array`

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0", "1"};
    }
}
```

## `List`

```java
public static class Example {
    public static void main(String[] args) {

        // Initialize ["0", "1"]
        List<String> l1 = Arrays.asList("0", "1");
        ArrayList<String> al1 = new ArrayList<>(Arrays.asList("0", "1"));
        ArrayList<String> al2 = new ArrayList<>(){{
            add("0");
            add("1");
        }};
        
        // Initialize ["0"]
        List<String> l2 = Collections.singletonList("0");
    }
}
```

# 类型转换 Convert

## `Array` to `Collection`

`Array` can only be converted to a `List` directly. We can then convert that `List` to other `Collection`'s.

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0"};

        // Convert to List
        List<String> l = Arrays.asList(a);

        // Convert to List and then to Collection
        ArrayList<String> al = new ArrayList<>(Arrays.asList(a));
    }
}
```

## `Vector` to `Array`

```java
public static class Example {
    public static void main(String[] args) {
        List<String> l = Arrays.asList("0", "1");

        String[] a1 = l.toArray(new String[0]);
        String[] a2 = l.stream().toArray(String[] ::new);
    }
}
```

## `Collection` to `Collection`

```java
public static class Example {
    public static void main(String[] args) {
        List<String> l = Arrays.asList("0", "1");

        // Constructor
        ArrayList<String> al = new ArrayList<>(l);
        LinkedList<String> ll = new LinkedList<>(l);
        HashSet<String> hs = new HashSet<>(l);
        TreeSet<String> tr = new TreeSet<>(l);
    }
}
```

# 排序 Sort

## `Array`

```java
public static class Example {
    public static void main(String[] args) {
        int[] a = new int[]{0};
        Arrays.sort(a);
        Arrays.sort(a, (o1, o2) -> o1 - o2);
        Arrays.sort(a, Collections.reverseOrder());
    }
}
```

# 深拷贝 Deep Copy
