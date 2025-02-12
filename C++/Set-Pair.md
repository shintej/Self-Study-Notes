# **C++ `set` and `pair` Functions Guide**

```cpp
#include <iostream>
#include <set>
#include <unordered_set>

using namespace std;

int main() {
    // 🌟 1️⃣ Ordered Set (std::set<T>) - Elements are stored in sorted order
    set<int> s;

    // 🔹 Insert elements
    s.insert(5);
    s.insert(2);
    s.insert(8);
    s.insert(5);  // Duplicates ignored

    // 🔹 Iterate over set
    cout << "Elements in set: ";
    for (int x : s) cout << x << " ";  // Output: 2 5 8
    cout << endl;

    // 🔹 Erase an element
    s.erase(5);

    // 🔹 Check if an element exists
    if (s.find(2) != s.end()) cout << "2 exists in the set\n";
    
    // 🔹 Lower and Upper Bound
    auto lb = s.lower_bound(3); // First element >= 3
    auto ub = s.upper_bound(3); // First element > 3

    if (lb != s.end()) cout << "Lower bound of 3: " << *lb << endl;
    if (ub != s.end()) cout << "Upper bound of 3: " << *ub << endl;

    // 🔹 Set size
    cout << "Set size: " << s.size() << endl;

    // 🔹 Check if set is empty
    cout << "Is set empty? " << (s.empty() ? "Yes" : "No") << endl;

    // 🔹 Clear the set
    s.clear();

    // 🌟 2️⃣ Unordered Set (std::unordered_set<T>) - No sorting, faster lookups
    unordered_set<int> us = {3, 1, 4, 1, 5, 9};

    cout << "Unordered Set elements: ";
    for (int x : us) cout << x << " ";
    cout << endl;

    // 🌟 3️⃣ Pair functions
    pair<int, string> p = {10, "Alice"};

    // 🔹 Access first and second element
    cout << "Pair first: " << p.first << ", second: " << p.second << endl;

    // 🌟 4️⃣ Pair inside Set
    set<pair<int, string>> sp;
    sp.insert({1, "one"});
    sp.insert({2, "two"});
    sp.insert({1, "duplicate"}); // Ignored

    // 🔹 Iterate over set of pairs
    cout << "Set of pairs:\n";
    for (auto x : sp) cout << x.first << " -> " << x.second << endl;

    return 0;
}
