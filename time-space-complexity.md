# Time and space complexity

Helps evaluate the efficiency and resource requirements of algorithms and data structures.

## Time complexity

Time complexity measures how the running time of an algorithm or program grows as the size of the input (usually denoted as "n") increases. It provides an estimation of the number of basic operations (such as comparisons, additions, or assignments) that an algorithm performs in relation to the input size.

Time complexity is often expressed using big O notation (O notation), which provides an upper bound on the growth rate of an algorithm's running time. Common time complexities include:


| Time Complexity     | Name              | Description                                     | Example                                         |
|---------------------|-------------------|-------------------------------------------------|-------------------------------------------------|
| O(1) | Constant Time     | The running time does not depend on the input size; it remains constant regardless of the input. | Accessing an element in an array by index. |
| O(log n) | Logarithmic Time | The running time grows logarithmically with the input size. | Common in algorithms like binary search. |
| O(n) | Linear Time       | The running time increases linearly with the input size. | Iterating through an array or list. |
| O(n log n) | Linearithmic Time | Common in sorting algorithms like merge sort and quicksort. | Sorting a list of elements. |
| O(n^2) | Quadratic Time   | The running time grows quadratically with the input size. | Common in nested loops. |
| O(2^n) | Exponential Time | The running time grows exponentially with the input size. | Typically associated with brute-force algorithms. |


### Relative time

**O(1) (Constant Time)**: The best possible time complexity, where the algorithm's running time doesn't depend on the input size. It's extremely efficient.

**O(log n) (Logarithmic Time)**: Very efficient and suitable for many practical purposes. Algorithms with O(log n) time complexity can handle large datasets with minimal increases in running time.

**O(n) (Linear Time)**: A linear increase in running time as the input size grows. This is less efficient than O(log n) for large datasets but can still be acceptable for moderate-sized inputs.

### log n

When we say an algorithm has O(log n) time complexity, it means that its running time grows very slowly as the input size (n) increases. The algorithm's efficiency becomes evident when dealing with large datasets, as it doesn't require linear or quadratic increases in time when the input size grows but instead experiences a logarithmic increase, which is much more favorable in terms of performance.

## Space complexity

Space complexity measures the amount of memory or space an algorithm or program requires to execute in relation to the input size. It accounts for the memory used by data structures, variables, and function call stacks during the execution of an algorithm.

Space complexity is also often expressed using big O notation. Common space complexities include:

| Space Complexity    | Name              | Description                                     | Example                                         |
|---------------------|-------------------|-------------------------------------------------|-------------------------------------------------|
| O(1) | Constant Space    | The space used remains constant, regardless of the input size. It usually means that the algorithm uses a fixed amount of memory. | Caching a single integer. |
| O(n) | Linear Space      | The space used grows linearly with the input size. Common in algorithms that store data in arrays or lists proportional to the input size. | Storing a list of n elements. |
| O(n^2) | Quadratic Space  | The space used grows quadratically with the input size. It may involve nested data structures. | Storing a 2D array with n rows and n columns. |
| O(log n) | Logarithmic Space | The space used grows logarithmically with the input size. Common in algorithms that use recursion but have a limited call stack depth. | Binary search with a recursive function. |
