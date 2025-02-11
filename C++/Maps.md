# C++ Maps: Detailed Guide

### Maps in C++
```cpp
#include <iostream>
#include <map>
#include <unordered_map>
using namespace std;

int main() {
    // 1. Basic Syntax & Initialization Methods
    map<int, string> m1;              // Empty map with integer keys and string values
    map<int, string> m2 = {{1, "one"}, {2, "two"}}; // Initialization with values

    // 2. Inserting Elements
    m1[1] = "apple";         // Insert using []
    m1.insert({2, "banana"});  // Insert using insert()
    m1.insert(make_pair(3, "cherry")); // Another way to insert
    m1.emplace(4, "date");     // More efficient insertion

    // 3. Accessing Elements
    cout << "Element with key 1: " << m1[1] << "\n"; // apple
    cout << "Element with key 2: " << m1.at(2) << "\n"; // banana

    // 4. Modifying Elements
    m1[1] = "avocado";  // Modify an existing key
    m1.erase(3);        // Erase element with key 3

    // 5. Searching in Maps
    if (m1.find(2) != m1.end()) {
        cout << "Key 2 found with value: " << m1[2] << "\n";
    }

    // 6. Iterating Over Maps
    cout << "Iterating using iterator: \n";
    for (auto it = m1.begin(); it != m1.end(); it++) {
        cout << "Key: " << it->first << ", Value: " << it->second << "\n";
    }

    cout << "Iterating using range-based loop: \n";
    for (const auto &p : m1) {
        cout << "Key: " << p.first << ", Value: " << p.second << "\n";
    }

    //Instead of using auto you can also use
    map<int, string> m1 = {{1, "one"}, {2, "two"}};

    // Instead of auto:
    map<int, string>::iterator it;
    for (it = m1.begin(); it != m1.end(); it++) {
        cout << "Key: " << it->first << ", Value: " << it->second << "\n";
    }
    
    // Range-based loop (explicit type)
    for (const pair<int, string> &p : m1) {
        cout << "Key: " << p.first << ", Value: " << p.second << "\n";
    } 


    // 7. Size & Capacity
    cout << "Size: " << m1.size() << "\n";
    cout << (m1.empty() ? "Map is empty" : "Map is not empty") << "\n";

    // 8. Unordered Maps (Faster, No Order)
    unordered_map<string, int> umap;
    umap["Alice"] = 25;
    umap["Bob"] = 30;
    
    cout << "Unordered Map Example: \n";
    for (const auto &p : umap) {
        cout << "Key: " << p.first << ", Value: " << p.second << "\n";
    }

    // 9. Clearing and Swapping
    map<int, string> tempMap = {{5, "grape"}, {6, "kiwi"}};
    m1.swap(tempMap);  // Swap contents of two maps
    m1.clear();        // Clears all elements

    // 10. Fast Input & Output for Maps
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

    int n;
    cin >> n;
    map<int, int> fastMap;

    for (int i = 0; i < n; i++) {
        int key, value;
        cin >> key >> value;
        fastMap[key] = value;
    }

    for (const auto &p : fastMap) {
        cout << "Key: " << p.first << ", Value: " << p.second << "\n";
    }
}
