---
title: "InsertionSort 삽입정렬"
date: 2019-07-28 23:45:28 -0400
categories: algorithm
---

삽입정렬은 배열의 앞에서부터 차례대로 이미 정렬된 배열 부분과 차례차례 비교하여 자신의 위치를 찾아 삽입하는 방법
비교대상인 왼쪽에 놓여진 배열은 이미 정렬되어있다.

```Java

public class InsertionSort {
    public static void main(String[] args) {
        InsertionSort app = new InsertionSort();
        int[] array = {10, 3, 2, 4};
        app.printArray(app.getInsertionSortedArray(array));
    }

    public int[] getInsertionSortedArray(int[] array) {
        int size =  array.length;
        int temp;
        for(int i=1; i<size; i++) {
            for(int j=i-1; j>=0; j--) {
                if(array[j]>array[j+1]) {
                    temp = array[j+1];
                    array[j+1] = array[j];
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
