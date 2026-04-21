# NumPy Fundamentals — Learning Journal 

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-28a745?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

A progressive self-documented series of Jupyter Notebooks covering NumPy from first principles to intermediate-level numerical computing. Each notebook reflects what I explored, the mental models I built, and the performance patterns I internalized.

---

## About This Repository

NumPy underpins virtually every numerical and scientific Python library — Pandas, Scikit-learn, TensorFlow, and PyTorch all depend on it. This repository is my structured attempt to understand it deeply rather than just use it incidentally. The notebooks progress from basic array creation through broadcasting, advanced indexing, and practical applications.

---

## Notebook Index

| Notebook | Topic | Key Concepts Covered |
|---|---|---|
| `Numpy_01.ipynb` | Introduction and Array Creation | `np.array()`, `np.zeros()`, `np.ones()`, `np.arange()`, `np.linspace()` |
| `Numpy_02.ipynb` | Array Attributes and Data Types | `shape`, `ndim`, `dtype`, `size`, explicit dtype casting |
| `Numpy_03.ipynb` | Indexing and Slicing | 1D and 2D slicing, negative indexing, step slicing |
| `Numpy_04.ipynb` | Boolean and Fancy Indexing | Conditional masks, index arrays, filtering rows |
| `Numpy_05.ipynb` | Array Reshaping and Manipulation | `reshape()`, `flatten()`, `ravel()`, `transpose()`, `np.newaxis` |
| `Numpy_06.ipynb` | Mathematical and Statistical Operations | Universal functions (ufuncs), `np.mean()`, `np.std()`, `np.sum()` |
| `Numpy_07.ipynb` | Aggregation and Broadcasting | Axis-wise aggregation, broadcasting rules, shape compatibility |
| `Numpy_08.ipynb` | Random Module and Practical Examples | `np.random.seed()`, distributions, simulation, reproducibility |
| `Numpy_09.ipynb` | Advanced Operations and Applications | `np.linalg`, dot products, matrix operations, real-world use cases |

---

## What I Learned

### The ndarray vs Python Lists

The most important insight early on is *why* NumPy exists. Python lists are flexible but slow for numerical work — they store pointers to objects and cannot take advantage of CPU-level vectorization. NumPy's `ndarray` stores homogeneous data in contiguous memory blocks, which allows operations to run in compiled C code rather than interpreted Python. The practical result is that NumPy operations on large arrays can be 50–100x faster than equivalent Python loops.

### Array Attributes and Dtype Discipline

Every array has a `shape` (its dimensions as a tuple), an `ndim` (number of axes), and a `dtype` (the data type of its elements). I learned to always be explicit about `dtype` when creating arrays that will feed into models or statistical computations — allowing NumPy to infer `float64` vs `int32` vs `bool` without guidance causes subtle bugs that surface later.

### Indexing and Slicing

NumPy slicing returns **views**, not copies. Modifying a slice modifies the original array. This is intentional — it avoids memory duplication — but it is a common source of unexpected behavior. When a true copy is needed, `.copy()` must be called explicitly.

### Boolean and Fancy Indexing

Boolean indexing allows filtering arrays with conditions rather than explicit loops. Fancy indexing uses an array of integer indices to select elements in arbitrary order. Both return copies rather than views, which distinguishes them from standard slicing.

### Reshaping and the Memory Layout Model

`reshape()` changes the logical structure of an array without changing its data. It works because NumPy tracks shape and strides separately from the underlying data buffer. `flatten()` always returns a copy; `ravel()` returns a view when possible. `transpose()` reverses axes, which is essential when preparing data for matrix operations.

### Broadcasting

Broadcasting is the mechanism that allows NumPy to apply operations between arrays of different shapes without explicitly copying data. The rules are: dimensions are compared trailing-to-leading; a dimension of size 1 is stretched to match the other; dimensions that are absent are treated as size 1. Once these rules are understood, broadcasting reduces entire categories of explicit the loops.

### Aggregation Along Axes

The `axis` parameter in functions like `np.sum()`, `np.mean()`, and `np.max()` specifies *which dimension to collapse*. `axis=0` collapses rows (producing column-wise statistics); `axis=1` collapses columns (producing row-wise statistics). This is one of the most frequently misunderstood parameters in NumPy.

### Random Module and Reproducibility

Setting a random seed with `np.random.seed()` makes stochastic operations reproducible. This is essential for any simulation or machine learning experiment where results need to be compared or debugged consistently across runs.

---

## Setup and Installation

**Clone the repository**

```bash
git clone https://github.com/abhishekakhand737/NUMPY.git
cd NUMPY
```

**Install dependencies**

```bash
pip install numpy notebook
```

**Launch Jupyter**

```bash
jupyter notebook
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.x | Runtime environment |
| NumPy | N-dimensional array operations and numerical computing |
| Jupyter Notebook | Interactive development and inline documentation |

---

## Author

**Abhishek Akhand**
B.Tech — Artificial Intelligence and Data Science.

GitHub: [abhishekakhand737](https://github.com/abhishekakhand737)

---

*NumPy does not make you think less — it makes you think at the right level of abstraction.*
