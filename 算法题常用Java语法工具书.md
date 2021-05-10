# 初始化 Initialize

## `Array`

Use `{}`. `[]` must be empty.

`{}` 中列出初始化值。`[]`须为空。

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0", "1"};
    }
}
```

## `Collection`

Most `Collection<E>`'s has a constructor with a `Collection<? extends E>` parameter. Except `Stack`.

Compared to the plain `list.add("0");`, initialization using anonymous subclass `{{}}` has extra memory costs. 

`Collections` has static functions to create immutable `Collection`'s with only one element.

除`Stack`以外都有带`Collection<? extends E>`参数的构造函数。

与正常的`list.add("0");`语句相比，使用匿名内部类`{{}}`初始化会造成额外内存开销。

只有一个元素的不可变`Collection`可以使用`Collections`类中的几个静态函数进行初始化。

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

Compared to the plain `map.put("0", "0");`, initialization using anonymous subclass `{{}}` has extra memory costs. 

`Collections.singletonMap(...)` can be used to create immutable `Map` with only one key-value pair.

与正常的`map.put("0", "0");`语句相比，使用匿名内部类`{{}}`初始化会造成额外内存开销。

只有一对键值对的不可变`Map`可以使用`Collections.singletonMap(...)`进行初始化。

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

Also, `Array`'s of primitive data types like `int[]` cannot be converted to `List<Integer>` directly.

数组需要先转换为列表，再转换为其他`Collection`类型。基本类型数组（如`int[]`）不能以如下方法直接转为列表。

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

Use the constructor with `Collection<? extends E>` parameter, or `addAll(Collection<? extends E> c))`.

使用带`Collection<? extends E>`的构造函数，或`addAll(Collection<? extends E> c))`。

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

反转数组需要手写for循环，或者先转换为列表，反转后再转回来。

```java
public static class Example {
    public static void main(String[] args) {
        String[] a = new String[]{"0", "1"};

        // Manual reversion
        int len = a.length;
        for (int i = 0; i < len / 2; ++i) {
            String tmp = a[i];
            a[i] = a[len - i - 1];
            a[len - i - 1] = tmp;
        }

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
