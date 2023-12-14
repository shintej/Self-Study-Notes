## Structures
Essentially creating your own data-structure or variable
```c++
struct Point{
  int x;
  int y;
};

struct Circle{
  Point centre;
  double radius;
};
```
Naming conventional is to have a capital letter to start this
```c++
Circle c1;
c1.centre.x = 1;
c1.centre.y = 2;
c1.radius = 2;

// or
c1 = {{1,2},2};
```
Can copy structures 
//Circle c2;
//c2 = c1;

array of structures possible
```c++
Circle c[10];
//like int c[10] where every array element is int here every array element is structure circle
```
Pointers in struct:
```c++
struct Node{
  int data;
  Node *next;
};

//example code
struct Node* head = NULL;
void insert(int new_data) {
   struct Node* new_node = (struct Node*) malloc(sizeof(struct Node)); // or Node* new_node = new Node;
   new_node->data = new_data;
   new_node->next = head;
   head = new_node;
}
void display() {
   struct Node* ptr;
   ptr = head;
   while (ptr != NULL) {
      cout<< ptr->data <<" ";
      ptr = ptr->next;
   }
}
```
The structures can be combined with functions to make a big structure.  
If structures are being passed to function by reference use a "const" indicator so that memory overhead is reduced



