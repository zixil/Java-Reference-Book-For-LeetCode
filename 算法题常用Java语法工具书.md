# 初始化 Initialize

## `Array`

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0", "1"};
    }
}
```

## `Collection`

```java
public static class Example {
    public static void main(String[] args) {
        // List
        List<String> l1 = Arrays.asList("0", "1");
        ArrayList<String> al1 = new ArrayList<>(Arrays.asList("0", "1"));
        ArrayList<String> al2 = new ArrayList<>(){{
            add("0");
            add("1");
        }};
        // Singleton List
        List<String> l2 = Collections.singletonList("0");

        // Set
        HashSet<String> hs1 = new HashSet<String>(Arrays.asList("0", "1"));
        // Singleton Set
        Set<String> s2 = Collections.singleton("0");
    }
}
```

## `Map`

```java
public static class Example {
    public static void main(String[] args) {
        HashMap<String, String> m1 = new HashMap<>() {{
            put("0", "0");
            put("1", "1");
        }};
        // Singleton Map
        Map<String, String> m2 = Collections.singletonMap("0", "0");
    }
}
```

# 类型转换 Convert

## `Array` to `Collection`

`Array` can only be converted to a `List` directly. We can then convert that `List` to other `Collection`'s.

Also, `Array`'s like `int[]` cannot be converted to `List<Integer>` directly.

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

## `Collection` to `Array`

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

        // Stack doesn't have non-empty constructor
        Stack<String> s = new Stack<>();
        s.addAll(l);
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

        // reverse
        Arrays.sort(a, Collections.reverseOrder());
        Arrays.sort(a, (o1, o2) -> o2 - o1);
    }
}
```

## `List`

```java
public static class Example {
    public static void main(String[] args) {
        ArrayList<Integer> al = new ArrayList<>(Arrays.asList(1, 2));

        al.sort(Comparator.naturalOrder());
        al.sort((o1, o2) -> o1 - o2);
        Collections.sort(al);
        Collections.sort(al, (o1, o2) -> o1 - o2);

        // reverse
        al.sort(Comparator.reverseOrder());
        al.sort((o1, o2) -> o2 - o1);
        Collections.sort(al, Collections.reverseOrder());
        Collections.sort(al, (o1, o2) -> o2 - o1);
    }
}
```

## `Stack`

```java
public static class Example {
    public static void main(String[] args) {
        String<Integer> s = new Stack<>();
        s.add(Arrays.asList(1, 2));

        s.sort(Comparator.naturalOrder());
        s.sort((o1, o2) -> o1 - o2);

        // reverse
        s.sort(Collections.reverseOrder());
        s.sort((o1, o2) -> o2 - o1);
    }
}
```

# 反转 Reverse

## `List`

```java
public static class Example {
    public static void main(String[] args) {
        List<Integer> l = Arrays.asList(1, 2);

        Collections.reverse(l);
    }
}
```

## `Array`

**`Array` has to be reversed manually**. Another choice is to convert it to a `List` at first.

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0", "1"};

        // Convert to List
        List<String> l = Arrays.asList(a);

        // Reverse the List
        Collections.reverse(l);

        // Convert back to Array
        a = l.toArray(new String[0]);
    }
}
```

# 深拷贝 Deep Copy
