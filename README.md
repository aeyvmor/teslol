# 🧾 C++ EXAM CHEAT SHEET

## ⚙️ 1. Dynamic Arrays
Dynamic arrays are arrays whose size is decided during runtime. They are created using the `new` keyword and deleted using `delete[]`.

```cpp
int size;
cout << "Enter size: ";
cin >> size;

int* arr = new int[size]; // create dynamic array
for (int i = 0; i < size; i++) {
    cout << "Enter element " << i + 1 << ": ";
    cin >> arr[i]; // or *(arr + i)
}
delete[] arr; // free memory
```

**Key points:**
* `new` allocates memory.
* `delete[]` releases memory.
* Use pointer arithmetic like `*(arr + i)` for access.

---

## 🧭 2. Pointers
Pointers are variables that store memory addresses.

```cpp
int x = 10;
int* p = &x;   // p stores the address of x
cout << *p;    // *p dereferences the pointer → prints 10
```

**Common pointer operations:**

| Symbol | Meaning |
|--------|---------|
| `&` | Address of variable |
| `*` | Dereference (access value) |
| `p + 1` | Move pointer to next memory location |
| `*(arr + i)` | Same as `arr[i]` |

---

## 🔁 3. Loops
Loops let you repeat actions.

### For loop
```cpp
for (int i = 0; i < 5; i++) {
    cout << i << " ";
}
```

### While loop
```cpp
int i = 0;
while (i < 5) {
    cout << i << " ";
    i++;
}
```

### Do-While loop
```cpp
int i = 0;
do {
    cout << i << " ";
    i++;
} while (i < 5);
```

---

## 🔠 4. ASCII Code
ASCII assigns numbers to characters. For example, `'A' = 65`, `'a' = 97`, `'0' = 48`.

```cpp
char ch = 'A';
cout << "ASCII of " << ch << " = " << int(ch) << endl;
```

**Quick tip:** You can convert uppercase to lowercase using ASCII math:
```cpp
ch = ch + 32; // 'A' → 'a'
```

---

## ⚡ 5. Exception Handling
Used to catch runtime errors (like division by zero). Use `try`, `throw`, and `catch`.

```cpp
try {
    if (b == 0) throw runtime_error("Cannot divide by zero!");
    cout << a / b;
} 
catch (exception& e) {
    cout << "Error: " << e.what();
}
```

---

# 💻 SAMPLE PROGRAMS

## 🧮 SAMPLE PROGRAM 1 — Miles Per Gallon (Dynamic Arrays + Pointers + Try/Catch)
This example computes Miles Per Gallon (MPG) while demonstrating dynamic arrays, pointer arithmetic, and exception handling.

```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

int main() {
    int size;
    cout << "Enter number of trips: ";
    cin >> size;

    double* miles = new double[size];
    double* gallons = new double[size];
    double* mpg = new double[size];

    try {
        cout << "\nEnter miles for each trip:\n";
        for (int i = 0; i < size; i++) {
            cout << "Miles[" << i << "]: ";
            cin >> *(miles + i);
        }

        cout << "\nEnter gallons for each trip:\n";
        for (int i = 0; i < size; i++) {
            cout << "Gallons[" << i << "]: ";
            cin >> *(gallons + i);
        }

        for (int i = 0; i < size; i++) {
            if (*(gallons + i) == 0)
                throw runtime_error("Division by zero!");
            *(mpg + i) = *(miles + i) / *(gallons + i);
        }

        cout << "\nMiles per Gallon (MPG):\n";
        for (int i = 0; i < size; i++) {
            cout << "Trip " << i + 1 << ": " << *(mpg + i) << " MPG\n";
        }
    } 
    catch (exception& e) {
        cout << "\nError: " << e.what() << endl;
    }

    delete[] miles;
    delete[] gallons;
    delete[] mpg;

    return 0;
}
```

---

## 🔤 SAMPLE PROGRAM 2 — ASCII Display using Pointers
This one combines loops, pointers, and ASCII concepts.

```cpp
#include <iostream>
using namespace std;

int main() {
    int size;
    cout << "Enter number of characters: ";
    cin >> size;

    char* letters = new char[size];

    cout << "\nEnter characters:\n";
    for (int i = 0; i < size; i++) {
        cout << "Letter[" << i << "]: ";
        cin >> *(letters + i);
    }

    cout << "\nASCII Values:\n";
    for (int i = 0; i < size; i++) {
        cout << *(letters + i) << " = " << int(*(letters + i)) << endl;
    }

    delete[] letters;
    return 0;
}
```

---

# ✨ QUICK REVIEW TIPS

✅ **Dynamic Array Syntax:**
```cpp
type* ptr = new type[size];
delete[] ptr;
```

✅ **Pointer Rule:** `arr[i] == *(arr + i)`

✅ **Try–Catch:** Always use when dividing or handling risky input.

✅ **Loop Rule:** Always start loops at `i = 0; i < size; i++`.

✅ **ASCII Tip:** `'A' + 32 = 'a'` → `'a' - 32 = 'A'`

---

# 🧠 Summary
If your written exam asks for a short program:
* Expect array input/output, pointer use, and possibly division.
* Use `try/catch` to handle divide-by-zero cases.
* Review ASCII values, loop basics, and dynamic memory allocation.

---

**Good luck on your exam! 🚀**