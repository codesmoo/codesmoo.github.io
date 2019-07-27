---
title: "SelectionSort 선택정렬"
date: 2019-07-27 22:50:28 -0400
categories: algorithm
---

선택정렬은 최소값을 찾고 최소값을 맨 앞에 있는 값의 위치를 교환한다.

```Java
public class SelectionSort {
    public static void main(String[] args) {
        SelectionSort app = new SelectionSort();
        int[] array = {10, 3, 2, 4};
        app.printArray(app.getSelectionSortedArray(array));
    }

    public int[] getSelectionSortedArray(int[] array) {

        int least;
        int temp;
        int size = array.length;

        for (int i = 0; i < size; i++) {
            temp = i;
            for (int j = i; j < size - 1; j++) {
                if (array[j] > array[j + 1]) {
                    temp = j + 1;
                }
            }
            least = array[temp];
            array[temp] = array[i];
            array[i] = least;
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
