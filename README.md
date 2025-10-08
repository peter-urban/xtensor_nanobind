# xtensor_nanobind

**Nanobind bindings for an xtensor/NumPy-compatible `pytensor`, supporting in-place NumPy array operations using xtensor.**

---

### ⚙️ Overview
`xtensor_nanobind` provides lightweight C++20 header-only nanobind bindings that allow for inplace operations on numpy arrays using xtensr,
This code was derived with assistance from ChatGPT-5 Codex, using xtensor-python's pytensor.hpp, pycontainer.hpp, and related components as example.  *


### 🧠 Note
This file was initially drafted with the assistance of *ChatGPT5-Codex* and may contain AI-generated phrasing. 
The pytensor class may still not support all xtensor features or may show some performance issues. Let me know if you detect any issues.

---

### 📦 Installation
This is a **header-only** project. Download the header file and include it in your nanobind module.

**Requirements:**
- C++20 compiler  
  *(tested with GCC 14, Clang 16–17, and Clang-CL 19)*

---

### 🚀 Usage

- **`pytensor` class** — compatible with `xt::xtensor`, allowing **NumPy array access by reference** for **in-place** operations and zero-copy performance.  
  *(Namespace: `xt::nanobind::pytensor`)*
- **Type casters** for:
  - `xt::xtensor` — provides automatic data conversion (copy/move semantics)
  - `pytensor` expressions — supports in-place and reference-based interaction with NumPy arrays

---

### 🧩 Example

```cpp
#include <nanobind/nanobind.h>
#include <nanobind/ndarray.h>
#include "xtensor_nanobind.hpp"  // Include the header



nanobind::module_ m("example", "Example module using pytensor");

// Function that doubles all elements of a NumPy array *in-place*
m.def("double_inplace", [](xt::nanobind::pytensor<double, 2>& arr) {
    arr *= 2.0;
});
