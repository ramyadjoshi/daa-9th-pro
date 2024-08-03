# daa-9th-pro
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
void selectionSort(int arr[], int n)
{
    int i, j, min_idx;
    for (i = 0; i < n-1; i++)
    {
        min_idx = i;  
        for (j = i+1; j < n; j++)
        {
            if (arr[j] < arr[min_idx])
            {
                min_idx = j;  // Update min_idx if a smaller element is found
            }
        }
        int temp = arr[min_idx];
        arr[min_idx] = arr[i];
        arr[i] = temp;
    }
}
void generateRandomNumbers(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        arr[i] = rand() % 10000;  // Generate random numbers between 0 and 9999
    }
}
int main()
{
    int n;
    printf("Enter number of elements: ");
    scanf("%d", &n);  // Read the number of elements from the user
    if (n <= 5000)
    {
        printf("Please enter a value greater than 5000\n");
        return 1;  // Exit if the number of elements is not greater than 5000
    }
    int *arr = (int *)malloc(n * sizeof(int));
    if (arr == NULL)
    {
        printf("Memory allocation failed\n");
        return 1;  // Exit if memory allocation fails
    }
    generateRandomNumbers(arr, n);
    clock_t start = clock();
    selectionSort(arr, n);
    clock_t end = clock();
    double time_taken = ((double)(end - start)) / CLOCKS_PER_SEC;
    printf("Time taken to sort %d elements: %f seconds\n", n, time_taken);
    free(arr);
    return 0;
}

OUTPUT
Enter number of elements: 6000
Time taken to sort 6000 elements: 0.031000 seconds

********************************************************************


Enter number of elements: 7000
Time taken to sort 7000 elements: 0.034000 seconds

********************************************************************


Enter number of elements: 8000
Time taken to sort 8000 elements: 0.047000 seconds

********************************************************************


Enter number of elements: 9000
Time taken to sort 9000 elements: 0.052000 seconds

********************************************************************

Enter number of elements: 10000
Time taken to sort 10000 elements: 0.077000 seconds
  ---------------for graph go to online matplotlib compiler---------
  import matplotlib.pyplot as plt

# data collected
n_values = [6000, 7000, 8000, 9000, 10000]
time_taken = [0.031000, 0.034000, 0.047000, 0.052000, 0.077000]  # replace with actual times recorded
plt.plot(n_values, time_taken, marker='o')
plt.title('Selection Sort Time Complexity')
plt.xlabel('Number of Elements (n)')
plt.ylabel('Time taken (seconds)')
plt.grid(True)
plt.show()
![image](https://github.com/user-attachments/assets/d0e839c4-2872-47f3-8d10-7a74f07cf191)
