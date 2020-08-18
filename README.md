# binary-using-sll
#include<stdio.h> 
#include<stdlib.h> 
  
struct Node 
{ 
    int data; 
    struct Node* next; 
}; 
  
Node *newNode(int x) 
{ 
    struct Node* temp = new Node; 
    temp->data = x; 
    temp->next = NULL; 
    return temp; 
} 
  
struct Node* middle(Node* start, Node* last) 
{ 
    if (start == NULL) 
        return NULL; 
  
    struct Node* slow = start; 
    struct Node* fast = start -> next; 
  
    while (fast != last) 
    { 
        fast = fast -> next; 
        if (fast != last) 
        { 
            slow = slow -> next; 
            fast = fast -> next; 
        } 
    } 
  
    return slow; 
} 
 
struct Node* binarySearch(Node *head, int value) 
{ 
    struct Node* start = head; 
    struct Node* last = NULL; 
  
    do
    { 
        Node* mid = middle(start, last); 
 
        if (mid == NULL) 
            return NULL; 
 
        if (mid -> data == value) 
            return mid; 
 
        else if (mid -> data < value) 
            start = mid -> next; 
  

        else
            last = mid; 
  
    } while (last == NULL || 
             last != start); 
    return NULL; 
} 
int main() 
{ 
    Node *head = newNode(1); 
    head->next = newNode(4); 
    head->next->next = newNode(7); 
    head->next->next->next = newNode(8); 
    head->next->next->next->next = newNode(9); 
    head->next->next->next->next->next = newNode(10); 
    int value = 7; 
    if (binarySearch(head, value) == NULL) 
        printf("Value not present\n"); 
    else
        printf("Present"); 
    return 0; 
} 
