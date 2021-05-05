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
        List<String> l = Arrays.asList("0", "1");
        ArrayList<String> al1 = new ArrayList<>(Arrays.asList("0", "1"));
        ArrayList<String> al2 = new ArrayList<>(){{
            add("0");
            add("1");
        }};
    }
}
```

#类型转换 Convert

## `Array` to `List`

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0"};
        List<String> l = Arrays.asList(a);
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

## `Collection` to `Array`

# 排序 Sort

## `Array`

```java
public static class Example {
    public static void main(String[] args) {
        int[] a = new int[]{0};
        Arrays.sort(a);
        Arrays.sort(a, (o1, o2) -> o1 - o2);
        Arrays.sort();
    }
}
```

# 深拷贝 Deep Copy
