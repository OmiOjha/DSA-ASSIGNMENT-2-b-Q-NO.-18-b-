In C, lists can be represented using arrays for simple scenarios where the size is known or can be managed. Here are basic list operations that can be performed using arrays:

1.Creating a List: Declaring an array and initializing it.
2.Inserting Elements: Adding elements at specific positions.
3.Deleting Elements: Removing elements from specific positions.
4.Searching Elements: Finding the index of a specific element.
5.Updating Elements: Changing the value of elements at specific positions.
6.Traversing: Displaying all elements of the list.

C Program Demonstrating List Operations Using Arrays:


#include <stdio.h>

#define MAX_SIZE 100  // Define the maximum size of the list

// Function to display the list elements
void displayList(int arr[], int size) {
   
    printf("List: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Function to insert an element at a specific position
void insertElement(int arr[], int *size, int element, int position) {
    
    if (*size >= MAX_SIZE) {
        printf("List is full, cannot insert element.\n");
        return;
    }
    
    if (position < 0 || position > *size) {
        printf("Invalid position!\n");
        return;
    }

    // Shift elements to the right
    for (int i = *size; i > position; i--) {
        arr[i] = arr[i - 1];
    }
    arr[position] = element;
    (*size)++;
    printf("Element %d inserted at position %d.\n", element, position);
}

// Function to delete an element from a specific position
void deleteElement(int arr[], int *size, int position) {
    
    if (*size <= 0) {
        printf("List is empty, cannot delete element.\n");
        return;
    }
    
    if (position < 0 || position >= *size) {
        printf("Invalid position!\n");
        return;
    }

    printf("Element %d deleted from position %d.\n", arr[position], position);

    // Shift elements to the left
    for (int i = position; i < *size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    (*size)--;
}

// Function to search for an element in the list
int searchElement(int arr[], int size, int element) {
    
    for (int i = 0; i < size; i++) {
        if (arr[i] == element) {
            return i;  // Return the index of the element
        }
    }
    return -1;  // Element not found
}

// Function to update an element at a specific position
void updateElement(int arr[], int size, int position, int newElement) {
   
    if (position < 0 || position >= size) {
        printf("Invalid position!\n");
        return;
    }
    printf("Element at position %d updated from %d to %d.\n", position, arr[position], newElement);
    arr[position] = newElement;
}

int main() {
    
    int arr[MAX_SIZE];
    int size = 0;  // Current size of the list

    // Initial list setup
    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;
    size = 3;

    displayList(arr, size);

    // Inserting elements
    insertElement(arr, &size, 15, 1);  // Insert 15 at position 1
    displayList(arr, size);

    // Deleting elements
    deleteElement(arr, &size, 2);  // Delete element at position 2
    displayList(arr, size);

    // Searching for an element
    int index = searchElement(arr, size, 20);
    if (index != -1) {
        printf("Element 20 found at position %d.\n", index);
    } else {
        printf("Element 20 not found in the list.\n");
    }

    // Updating an element
    updateElement(arr, size, 1, 25);  // Update element at position 1 to 25
    displayList(arr, size);

    return 0;
}


Explanation of Operations
1.Initialize List:

a.We start by initializing an array arr with a size of 3 and some initial values {10, 20, 30}.

2.Insert Element:
a.The insertElement function takes the element to be inserted, the position where it should be inserted, and shifts elements to the right from that position.
b.Example: Inserting 15 at position 1 results in {10, 15, 20, 30}.

3.Delete Element:
a.The deleteElement function removes an element at the specified position and shifts subsequent elements to the left.
b.Example: Deleting the element at position 2 (value 20) results in {10, 15, 30}.

4.Search Element:
a.The searchElement function looks for a specified element and returns its index if found.
b.Example: Searching for 20 returns 1 as the index.

5.Update Element:
a.The updateElement function modifies an element at a specified position with a new value.
b.Example: Updating the element at position 1 to 25 changes the list to {10, 25, 30}.

6.Display List:
a.The displayList function prints out the current elements in the list.
