# Contiguous Subarray Sum Checker

## Overview
This project determines if a contiguous subarray within a given array of integers sums up to a specified target. The solution is optimized for arrays with up to 100,000 elements.

## Problem Statement
Given an array of integers and a target sum, identify if there exists a contiguous subarray that sums up to the target. If such a subarray exists, return `true`; otherwise, return `false`.

### Example
- **Input:** 
  - `arr = [4, 2, 7, 1, 9, 5]`
  - `target = 17`
- **Output:** `true`
- **Explanation:** The subarray `[7, 1, 9]` sums to 17, which matches the target.

### Constraints
- Array length: 1 to 100,000 elements.
- Element values and target sum: -1,000,000,000 to 1,000,000,000.
- Expected Time Complexity: O(n)
- Expected Space Complexity: O(1)

## Approach
### Sliding Window Technique
1. **Initialization:** Start with two pointers, `start` and `end`, at the beginning of the array. Initialize `current_sum` to 0.
2. **Expand and Contract Window:** 
   - Expand the window by moving the `end` pointer and adding the current element to `current_sum`.
   - If `current_sum` exceeds the target, contract the window by moving the `start` pointer right and subtracting the element at `start` from `current_sum`.
   - If `current_sum` matches the target, return `true`.
3. **Continue until the `end` pointer reaches the end of the array.**
4. If no subarray is found, return `false`.

## Usage
### Installation
No installation is required. Simply open the `index.html` file in a web browser.

### Code

#### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contiguous Subarray Sum Checker</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Contiguous Subarray Sum Checker</h1>
        <input type="text" id="arrayInput" placeholder="Enter array elements separated by commas">
        <input type="number" id="targetInput" placeholder="Enter target sum">
        <button onclick="checkSubarraySum()">Check</button>
        <p id="result"></p>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

#### CSS
```css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    text-align: center;
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input {
    display: block;
    margin: 10px auto;
    padding: 10px;
    width: calc(100% - 40px);
}

button {
    padding: 10px 20px;
    background-color: #28a745;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

#result {
    margin-top: 20px;
    font-size: 1.2em;
}
```

#### JavaScript
```javascript
function checkSubarraySum() {
    const arr = document.getElementById('arrayInput').value.split(',').map(Number);
    const target = Number(document.getElementById('targetInput').value);
    const result = document.getElementById('result');

    let start = 0, current_sum = 0;

    for (let end = 0; end < arr.length; end++) {
        current_sum += arr[end];

        while (current_sum > target && start <= end) {
            current_sum -= arr[start];
            start++;
        }

        if (current_sum === target) {
            result.innerHTML = 'True';
            return;
        }
    }

    result.innerHTML = 'False';
}
```

## Conclusion
The Contiguous Subarray Sum Checker efficiently identifies if a contiguous subarray sums to a given target using the sliding window technique. The algorithm runs in linear time and uses constant space, making it suitable for large arrays. Simply enter the array and target in the provided inputs, and click "Check" to see the result.
