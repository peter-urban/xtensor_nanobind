# xtensor_nanobind

**Nanobind bindings for an xtensor/NumPy-compatible `pytensor`, supporting efficient in-place NumPy array operations.**

---

### ⚙️ Overview
`xtensor_nanobind` provides lightweight C++20 header-only bindings that integrate **xtensor**, **NumPy**, and **PyTensor** through **nanobind**.  
It enables **high-performance**, **in-place** operations on NumPy arrays from C++, while maintaining seamless interoperability between C++ and Python.

---

### 🧠 Note
This file was initially drafted with the assistance of *ChatGPT5-Codex* and may contain minor AI-generated phrasing.

---

### 📦 Installation
This library is **header-only** — simply download the header file and include it in your nanobind module.

**Requirements:**
- C++20 compiler  
  *(tested with GCC 14, Clang 16–17, and Clang-CL 19)*

---

### 🚀 Usage
Include the header in your C++ project to use the `pytensor` class for efficient C++ ↔ Python data exchange through nanobind.

**Features:**
- **`pytensor` class** — compatible with `xt::xtensor`, allowing **NumPy array access by reference** for **in-place** operations and zero-copy performance.  
  *(Namespace: `xt::nanobind::pytensor`)*
- **Type casters** for:
  - `xt::xtensor` — provides automatic data conversion (copy/move semantics)
  - `pytensor` expressions — supports efficient in-place and reference-based interaction with NumPy arrays

---

### 🧩 Quick Example

#### C++: Create a nanobind module using `pytensor`

```cpp
#include <nanobind/nanobind.h>
#include <nanobind/ndarray.h>
#include "xtensor_nanobind.hpp"  // Include the header



nanobind::module_ m("example", "Example module using pytensor");

// Function that doubles all elements of a NumPy array *in-place*
m.def("double_inplace", [](xt::nanobind::pytensor<double, 2>& arr) {
    arr *= 2.0;
});
