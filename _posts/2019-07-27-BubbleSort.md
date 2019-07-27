---
title: "BubbleSort "
date: 2019-07-27 22:42:28 -0400
categories: algorithm
---

버블정렬은 정렬 대상의 n번째 인덱스와 n+1번째 인덱스를 비교해서 큰값을 뒤로 보내는 방법.

```Java

public class BubbleSort {
    public static void main(String[] args) {
        BubbleSort application = new BubbleSort();
        int[] array = {10, 3, 2, 4};
        application.printArray(application.getBubbleSortedArray(array));

    }

    public int[] getBubbleSortedArray(int[] array) {
        int size = array.length;
        int temp;

        for (int i = size - 1; i > 0; i--) {
            for (int j = 0; j < i; j++) {
                if (array[j] > array[j + 1]) {
                    temp = array[j + 1];
                    array[j + 1] = array[j];
                    array[j] = temp;
                }
            }
        }

        return array;
    }

    public void printArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            if (i == array.length - 1) {
                System.out.print(array[i]);
                return;
            }
            System.out.print(array[i] + ",");
        }
    }
}
```
