---
title: "QuickSort 퀵정렬"
date: 2019-08-01 20:20:28 -0400
categories: algorithm
---

병합정렬과 마찬가지로 문제를 분할,정복 정렬하는 방법.
퀵정렬의 순서는
1.리스트에서 하나의 pivot을 정하고
2.이 pivot을 기준으로 두 개의 비균등한 크기로 분할한 다음
3.분할된 부분 리스트를 정렬하고
4.두 개의 정렬된 부분 리스트를 합한다

```Java
public class QuickSort {
    public static void main(String[] args) {
        QuickSort app = new QuickSort();
        int[] array = {10, 3, 9, 2, 5, 6, 16, 7, 20, 19};
        app.quickSorted(array, 0, array.length-1);
        app.printArray(array);
    }

    private int partition(int[] array, int left, int right) {
        int pivot =  array[right]; //정렬할 리스트의 가장 오른쪽 데이터를 pivot으로 선택
        int i = left-1;
        for(int j = left; j < right; j++) { //pivot 보다 작은값을 왼쪽으로 몰아넣는과정
                                            //pivot의 오른쪽에는 pivot보다 큰 값들이 있다.
            if(array[j]<=pivot) {
                i++;
                this.swap(array, i, j);
            }
        }

        //pivot보다 작은값으로 몰아넣었던 index(i)의 그 다음 자리(i+1)로 pivot을 swap
        this.swap(array, i+1, right);

        return i+1;
    }

    private void quickSorted(int[] array, int left, int right) {
        if(left<right) {
            int p = partition(array, left, right); //swap된 pivot 자리인 p에 해당하는 index는 fix 된다.
            quickSorted(array, left, p-1);  //fix된 pivot 왼편 정렬
            quickSorted(array, p+1, right);  //fix된 pivot 오른편 정렬
        }
    }

    private void printArray(int[] array) {
        for (int i = 0; i < array.length; i++) {
            if (i == array.length - 1) {
                System.out.print(array[i]);
                return;
            }
            System.out.print(array[i] + ",");
        }
    }

    private void swap(int[] array, int i, int j) {
        int temp = array[j];
        array[j] = array[i];
        array[i] = temp;
    }

}
```
