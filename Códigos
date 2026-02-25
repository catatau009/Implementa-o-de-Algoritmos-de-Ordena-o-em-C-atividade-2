#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// =============================
// Função para imprimir array
// =============================
void printArray(int arr[], int n) {
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

// =============================
// Função para copiar array
// =============================
void copyArray(int origem[], int destino[], int n) {
    for(int i = 0; i < n; i++)
        destino[i] = origem[i];
}

// =============================
// Bubble Sort
// =============================
void bubbleSort(int arr[], int n) {
    for(int i = 0; i < n-1; i++) {
        for(int j = 0; j < n-i-1; j++) {
            if(arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
}

// =============================
// Selection Sort
// =============================
void selectionSort(int arr[], int n) {
    for(int i = 0; i < n-1; i++) {
        int min = i;
        for(int j = i+1; j < n; j++) {
            if(arr[j] < arr[min])
                min = j;
        }

        int temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }
}

// =============================
// Insertion Sort
// =============================
void insertionSort(int arr[], int n) {
    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while(j >= 0 && arr[j] > key) {
            arr[j+1] = arr[j];
            j--;
        }
        arr[j+1] = key;
    }
}

// =============================
// Quick Sort
// =============================
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;

    for(int j = low; j < high; j++) {
        if(arr[j] < pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }

    int temp = arr[i+1];
    arr[i+1] = arr[high];
    arr[high] = temp;

    return i+1;
}

void quickSort(int arr[], int low, int high) {
    if(low < high) {
        int pi = partition(arr, low, high);

        quickSort(arr, low, pi-1);
        quickSort(arr, pi+1, high);
    }
}

// =============================
// Merge Sort
// =============================
void merge(int arr[], int left, int mid, int right) {

    int n1 = mid - left + 1;
    int n2 = right - mid;

    int L[n1], R[n2];

    for(int i = 0; i < n1; i++)
        L[i] = arr[left + i];

    for(int j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    int i = 0, j = 0, k = left;

    while(i < n1 && j < n2) {
        if(L[i] <= R[j])
            arr[k++] = L[i++];
        else
            arr[k++] = R[j++];
    }

    while(i < n1)
        arr[k++] = L[i++];

    while(j < n2)
        arr[k++] = R[j++];
}

void mergeSort(int arr[], int left, int right) {
    if(left < right) {

        int mid = (left + right) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid+1, right);

        merge(arr, left, mid, right);
    }
}

// =============================
// Shell Sort
// =============================
void shellSort(int arr[], int n) {

    for(int gap = n/2; gap > 0; gap /= 2) {

        for(int i = gap; i < n; i++) {

            int temp = arr[i];
            int j;

            for(j = i; j >= gap && arr[j-gap] > temp; j -= gap)
                arr[j] = arr[j-gap];

            arr[j] = temp;
        }
    }
}

// =============================
// Função para medir tempo
// =============================
void medirTempo(void (*funcao)(int[], int), int arr[], int n, char nome[]) {

    clock_t inicio, fim;

    inicio = clock();
    funcao(arr, n);
    fim = clock();

    double tempo = ((double)(fim - inicio)) / CLOCKS_PER_SEC;

    printf("\n%s executado em: %.6f segundos\n", nome, tempo);
}

// =============================
// Menu
// =============================
int main() {

    int tamanho = 10;

    int original[10] = {64, 34, 25, 12, 22, 11, 90, 88, 76, 50};
    int arr[10];

    int opcao;

    do {

        printf("\n===== MENU DE ORDENACAO =====\n");
        printf("1 - Bubble Sort\n");
        printf("2 - Selection Sort\n");
        printf("3 - Insertion Sort\n");
        printf("4 - Quick Sort\n");
        printf("5 - Merge Sort\n");
        printf("6 - Shell Sort\n");
        printf("7 - Executar TODOS\n");
        printf("0 - Sair\n");

        printf("Escolha: ");
        scanf("%d", &opcao);

        switch(opcao) {

            case 1:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);
                medirTempo(bubbleSort, arr, tamanho, "Bubble Sort");
                printArray(arr, tamanho);
                break;

            case 2:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);
                medirTempo(selectionSort, arr, tamanho, "Selection Sort");
                printArray(arr, tamanho);
                break;

            case 3:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);
                medirTempo(insertionSort, arr, tamanho, "Insertion Sort");
                printArray(arr, tamanho);
                break;

            case 4:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);

                clock_t inicio, fim;

                inicio = clock();
                quickSort(arr, 0, tamanho-1);
                fim = clock();

                printf("\nQuick Sort executado em: %.6f segundos\n",
                ((double)(fim - inicio))/CLOCKS_PER_SEC);

                printArray(arr, tamanho);
                break;

            case 5:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);

                inicio = clock();
                mergeSort(arr, 0, tamanho-1);
                fim = clock();

                printf("\nMerge Sort executado em: %.6f segundos\n",
                ((double)(fim - inicio))/CLOCKS_PER_SEC);

                printArray(arr, tamanho);
                break;

            case 6:
                copyArray(original, arr, tamanho);
                printArray(arr, tamanho);
                medirTempo(shellSort, arr, tamanho, "Shell Sort");
                printArray(arr, tamanho);
                break;

            case 7:

                copyArray(original, arr, tamanho);
                medirTempo(bubbleSort, arr, tamanho, "Bubble Sort");

                copyArray(original, arr, tamanho);
                medirTempo(selectionSort, arr, tamanho, "Selection Sort");

                copyArray(original, arr, tamanho);
                medirTempo(insertionSort, arr, tamanho, "Insertion Sort");

                copyArray(original, arr, tamanho);
                inicio = clock();
                quickSort(arr, 0, tamanho-1);
                fim = clock();
                printf("Quick Sort executado em: %.6f segundos\n",
                ((double)(fim - inicio))/CLOCKS_PER_SEC);

                copyArray(original, arr, tamanho);
                inicio = clock();
                mergeSort(arr, 0, tamanho-1);
                fim = clock();
                printf("Merge Sort executado em: %.6f segundos\n",
                ((double)(fim - inicio))/CLOCKS_PER_SEC);

                copyArray(original, arr, tamanho);
                medirTempo(shellSort, arr, tamanho, "Shell Sort");

                break;

        }

    } while(opcao != 0);

    return 0;
}
