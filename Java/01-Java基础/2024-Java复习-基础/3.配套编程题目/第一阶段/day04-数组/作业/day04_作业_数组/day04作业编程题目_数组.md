## 题目1:

```java
需求:
	请使用静态初始化的方式,创建一个长度为5的整数数组,并为数组中的元素赋值,
	遍历数组,在同一行打印所有元素,元素之间用空格隔开,
	比如1:如果数组为{1,2,3,4,5}打印结果:1 2 3 4 5
    比如2:如果数组为{1,2,3,4,5}打印结果:[1, 2, 3, 4, 5]
```

### 你的答案:

```java
public class Solution {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```



## 题目2

```java
需求:
	现有一个整数数组{100,50,90,60,80,70}。请编写代码，计算数组中的所有元素的和并打印。
```



### 你的答案:

```java
public class Solution {
    public static void main(String[] args) {
        int[] arr = {100,50,90,60,80,70};
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];
        }
        System.out.println(sum);
    }
}
```



## 题目3

```java
需求:
	现有一个整数数组{100,50,90,60,80,70}。请编写代码，计算数组中的所有元素的最小值并打印。
```



### 你的答案:

```java
public class Solution {
    public static void main(String[] args) {
        int[] arr = {100,50,90,60,80,70};
        int min = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i];
            }
        }
        System.out.println(min);
    }
}
```



## 题目4

```java
需求:
	现有一个整数数组{100,50,90,60,80,70}。请编写代码，计算数组中的所有元素的最大值并打印。
```



### 你的答案:

```java
public class Solution {
    public static void main(String[] args) {
        int[] arr = {100,50,90,60,80,70};
        int max = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println(max);
    }
}
```



## 题目5

```java
需求:
	现有一个整数数组{100,50,90,60,80,70}。
	请编写程序，计算去掉最大值和最小值后的平均值（不考虑小数部分）
```



### 你的答案:

```java
public class Solution {
    public static void main(String[] args) {
        int[] arr = {100,50,90,60,80,70};
        int max = arr[0];
        int min = arr[0];
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
            if (arr[i] < min) {
                min = arr[i];
            }
            sum += arr[i];
        }
        System.out.println((sum - max - min) / (arr.length - 2));
    }
}
```

