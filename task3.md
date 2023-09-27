# 3 алгоритми сортування мовою програмування Java

У цьому документі описано три алгоритми сортування, які можна реалізувати мовою програмування Java:

* **Сортування бульбашкою**
* **Сортування вибором**
* **Сортування злиттям**

## Сортування бульбашкою

Сортування бульбашкою - це найпростіший алгоритм сортування. Він працює, послідовно порівнюючи всі елементи масиву та обмінюючи місцями елементи, які знаходяться в неправильному порядку.

```java
public static void bubbleSort(int[] array) {
  for (int i = 0; i < array.length - 1; i++) {
    for (int j = 0; j < array.length - i - 1; j++) {
      if (array[j] > array[j + 1]) {
        int temp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = temp;
      }
    }
  }
}


 Сортування вибором

Сортування вибором працює, знаходячи найменший елемент у невідсортованому масиві та обмінюючи його з першим елементом у масиві. Потім алгоритм повторюється, знаходячи наступний найменший елемент і обмінюючи його з другим елементом у масиві.

java
public static void selectionSort(int[] array) {
  for (int i = 0; i < array.length - 1; i++) {
    int minIndex = i;
    for (int j = i + 1; j < array.length; j++) {
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }
    }

    int temp = array[i];
    array[i] = array[minIndex];
    array[minIndex] = temp;
  }
}


 Сортування злиттям

Сортування злиттям працює, розділяючи масив на два підмасиви, сортуючи кожен підмасив окремо, а потім об'єднуючи два відсортованих підмасиви в один відсортований масив.

java
public static void mergeSort(int[] array) {
  if (array.length <= 1) {
    return;
  }

  int mid = array.length / 2;
  int[] left = Arrays.copyOfRange(array, 0, mid);
  int[] right = Arrays.copyOfRange(array, mid, array.length);

  mergeSort(left);
  mergeSort(right);

  merge(left, right, array);
}

private static void merge(int[] left, int[] right, int[] array) {
  int i = 0, j = 0, k = 0;

  while (i < left.length && j < right.length) {
    if (left[i] <= right[j]) {
      array[k++] = left[i++];
    } else {
      array[k++] = right[j++];
    }
  }

  while (i < left.length) {
    array[k++] = left[i++];
  }

  while (j < right.length) {
    array[k++] = right[j++];
  }
}


 Висновок

Який алгоритм сортування вибрати, залежить від конкретних потреб вашої програми. Якщо вам потрібен простий алгоритм, який працює з невеликими масивами, то можете обрати сортування бульбашкою або сортування вибором. Якщо вам потрібен більш ефективний алгоритм, обирайте злиття.
