---
title: "MergeSort 병합정렬"
date: 2019-08-01 17:30:28 -0400
categories: algorithm
---

병합정렬
divide(분할), conquer(정복), merge(병합) 으로 구성된다.
하나의 리스트를 균등하게 분할하고 분할된 부분 리스트를 정렬한 다음, 두 개의 정렬된 부분 리스트를 합하여 전체가 정렬된 리스트가 되게 하는 방법.

```Java

public class MergeSort {
    public static int[] sortedArray = new int[8];

    public static void main(String[] args) {
        MergeSort app = new MergeSort();
        int[] array = {10, 3, 2, 17, 15, 22, 1, 4};
        int size = array.length;
        app.mergeSort(array, 0, size - 1);
        app.printArray(sortedArray);
    }

    public void mergeSort(int[] array, int left, int right) {
        int mid;
        if (left < right) {
            mid = (left + right) / 2;               //divide(분할) 분할 기점인 중간위치를 계산
            mergeSort(array, left, mid);            //conquer(정복) 앞쪽 부분 정렬
            mergeSort(array, mid + 1, right);  //conquer(정복)뒤쪽 부분 정렬
            merge(array, left, mid, right);         //merge(병합) 
        }
    }

    public void merge(int[] array, int left, int mid, int right) {
        int i = left;
        int j = mid + 1;
        int k = left;

        while (i <= mid && j <= right) {
            if (array[i] <= array[j]) {
                sortedArray[k++] = array[i++];
            } else {
                sortedArray[k++] = array[j++];
            }
        }

        //정렬 후 남은 값들을 복사
        while (i <= mid) {
            sortedArray[k++] = array[i++];
        }

        // 재복사는 sortedArray에 정렬된 상태 만큼만 복사를 한다.
        for (int l = left; l < k; l++) {
            array[l] = sortedArray[l];
        }
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
