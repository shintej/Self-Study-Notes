# **Stack and Queue in C++ (Code Examples)**

```cpp
#include <iostream>
#include <stack>
#include <queue>

using namespace std;

int main() {
    // ********** STACK EXAMPLE (LIFO) **********
    stack<int> s;

    // Pushing elements into the stack
    s.push(10);
    s.push(20);
    s.push(30);

    cout << "Stack Operations:" << endl;
    cout << "Top element: " << s.top() << endl; // 30

    // Removing top element
    s.pop();
    cout << "Top after pop: " << s.top() << endl; // 20

    // Stack size
    cout << "Stack size: " << s.size() << endl; // 2

    // Checking if stack is empty
    cout << (s.empty() ? "Stack is empty" : "Stack is not empty") << endl;

    cout << "-----------------------------" << endl;

    // ********** QUEUE EXAMPLE (FIFO) **********
    queue<int> q;

    // Enqueue (push) elements
    q.push(1);
    q.push(2);
    q.push(3);

    cout << "Queue Operations:" << endl;
    cout << "Front element: " << q.front() << endl; // 1
    cout << "Back element: " << q.back() << endl;   // 3

    // Removing front element
    q.pop();
    cout << "Front after pop: " << q.front() << endl; // 2

    // Queue size
    cout << "Queue size: " << q.size() << endl; // 2

    // Checking if queue is empty
    cout << (q.empty() ? "Queue is empty" : "Queue is not empty") << endl;

    return 0;
}
