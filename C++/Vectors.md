# C++ Vectors: Detailed Guide

### Vectors in C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    // 1. Basic Syntax & Initialization Methods
    vector<int> v1;               // Empty vector
    vector<int> v2(5);            // Vector of size 5, default-initialized (zeroes)
    vector<int> v3(5, 100);       // Vector of size 5, all elements initialized to 100
    vector<int> v4 = {1, 2, 3};   // List initialization
    vector<int> v5(v4);           // Copy constructor
    vector<int> v6(v4.begin(), v4.begin() + 2); // Partial copy of first 2 elements

    // 2. Accessing Elements
    cout << "First Element: " << v4[0] << "\n";      // 1
    cout << "Second Element (safe access): " << v4.at(1) << "\n"; // 2
    cout << "Front Element: " << v4.front() << "\n"; // 1
    cout << "Last Element: " << v4.back() << "\n";   // 3

    // 3. Modifying Vectors
    v4.push_back(4);   // {1, 2, 3, 4}
    v4.pop_back();     // {1, 2, 3}

    v4.insert(v4.begin() + 1, 10);   // {1, 10, 2, 3}
    v4.insert(v4.begin(), 3, 100);   // {100, 100, 100, 1, 10, 2, 3}
    
    v4.erase(v4.begin() + 1);  // Removes second element
    v4.erase(v4.begin(), v4.begin() + 2); // Removes first two elements
    v4.clear();  // Clears all elements

    // 4. Size & Capacity
    vector<int> v = {1, 2, 3};
    cout << "Size: " << v.size() << "\n";
    cout << "Capacity: " << v.capacity() << "\n";
    cout << "Max Size: " << v.max_size() << "\n";
    cout << (v.empty() ? "Vector is empty" : "Vector is not empty") << "\n";
    v.shrink_to_fit();

    // 5. Iterating Over Vectors
    vector<int> iterVector = {10, 20, 30, 40};
    cout << "Iteration using iterator: ";
    for (auto it = iterVector.begin(); it != iterVector.end(); it++) {
        cout << *it << " ";
    }
    cout << "\n";

    cout << "Iteration using range-based loop: ";
    for (int val : iterVector) {
        cout << val << " ";
    }
    cout << "\n";

    // 6. Sorting & Reversing
    vector<int> sortVector = {3, 1, 4, 5, 2};
    sort(sortVector.begin(), sortVector.end());  // {1, 2, 3, 4, 5}
    reverse(sortVector.begin(), sortVector.end());  // {5, 4, 3, 2, 1}

    // 7. Searching in Vectors
    if (binary_search(sortVector.begin(), sortVector.end(), 3)) {
        cout << "Element 3 found in sorted vector\n";
    }

    auto it = find(sortVector.begin(), sortVector.end(), 3);
    if (it != sortVector.end()) {
        cout << "Element 3 found at index: " << it - sortVector.begin() << "\n";
    }

    // 8. Other Useful Functions
    cout << "Min element: " << *min_element(sortVector.begin(), sortVector.end()) << "\n";
    cout << "Max element: " << *max_element(sortVector.begin(), sortVector.end()) << "\n";
    cout << "Occurrences of 3: " << count(sortVector.begin(), sortVector.end(), 3) << "\n";

    // 9. 2D Vectors (Matrix)
    vector<vector<int>> matrix(3, vector<int>(4, 0));  // 3x4 matrix filled with 0
    matrix[1][2] = 5;  // Assign value

    // 10. Fast Input & Output with Vectors
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

    int n;
    cin >> n;
    vector<int> fastInputVector(n);
    
    for (int &x : fastInputVector) cin >> x;  // Fast input
    for (int x : fastInputVector) cout << x << " ";  // Fast output
}
```
