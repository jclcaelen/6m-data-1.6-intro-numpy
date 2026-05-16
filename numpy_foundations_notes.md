# NumPy Foundations — Broadcasting, Indexing, and Statistical Intuition

## 1. Why NumPy is Fast (vs Python Lists)

NumPy arrays are faster than Python lists because:
- Contiguous memory layout
- Homogeneous data types (fixed dtype)

Python list:
- Stores pointers to Python objects
- Elements are scattered in memory

NumPy array:
- Stores raw values in contiguous memory
- Fixed-size elements (e.g. int64)
- Cache-friendly and SIMD-optimised

---

## 2. Object dtype vs Numeric dtype

dtype=object behaves like Python lists:
- Each element is a Python object reference
- Loses SIMD/vectorisation benefits

Avoid dtype=object for numerical work.

---

## 3. Shape Fundamentals

1D array:
(5,) → single axis

2D array:
(rows, columns)

---

## 4. Indexing Types

### Basic indexing
- Integer → reduces dimension
- Slice (:) → preserves dimension

arr[1] → reduces dimension
arr[1:2] → preserves dimension

### Fancy indexing
Triggered by lists/arrays/boolean masks:
arr[[0,3]]

- Arbitrary selection
- Returns COPY

---

## 5. np.ix_

Fancy indexing:
arr[[0,3],[1,4]] → pairwise selection

np.ix_:
arr[np.ix_([0,3],[1,4])] → Cartesian product

---

## 6. Broadcasting

(5,3) - (3,) aligns from right side.
Smaller array is logically expanded.

---

## 7. Centering

scores - mean(axis=0)

Removes subject bias:
- positive → above average
- negative → below average

---

## 8. Clipping

np.clip(scores,0,100)

Enforces real-world constraints:
- prevents invalid outputs
- ensures bounded values

---

## 9. A/B Testing

Conversion rate = mean(binary array)

Mean of 0/1 = probability estimate.

---

## 10. Key Mental Models

- Lists = pointers
- NumPy = contiguous memory
- Integer index = reduce axis
- Slice = preserve axis
- Fancy indexing = copy
- Broadcasting = shape alignment
