# String Transformation Challenge

## Overview
This project transforms a given string based on its length using specified rules. The transformation rules depend on the divisibility of the string length by 3, 5, and 15.

## Problem Statement
Given a string, apply the following transformations based on its length:
- If the length is divisible by 3, reverse the entire string.
- If the length is divisible by 5, replace each character with its ASCII code.
- If the length is divisible by both 3 and 5 (i.e., 15), perform both operations in the specified order (reverse first, then replace with ASCII codes).

### Examples
1. **Input:** `"Hamburger"`
   - **Output:** `"regrubmaH"`
   - **Explanation:** The length is 9, divisible by 3 but not by 5 or 15. Hence, the string is reversed.

2. **Input:** `"Pizza"`
   - **Output:** `"80 105 122 122 97"`
   - **Explanation:** The length is 5, divisible by 5 but not by 3 or 15. Hence, each character is replaced by its ASCII code.

3. **Input:** `"Chocolate Chip Cookie"`
   - **Output:** `"eikooCpihCetalocohC"`
   - **Explanation:** The length is 21, divisible by 3 but not by 5 or 15. Hence, the string is reversed.

### Constraints
- The string will only contain alphanumeric characters and spaces.
- The length of the string will be between 1 and 1000.
- Expected Time Complexity: O(n), where n is the length of the string.
- Expected Space Complexity: O(n), where n is the length of the string.

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
    <title>String Transformation Challenge</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>String Transformation Challenge</h1>
        <input type="text" id="stringInput" placeholder="Enter your string here">
        <button onclick="transformString()">Transform</button>
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
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

#result {
    margin-top: 20px;
    font-size: 1.2em;
}
```

#### JavaScript
```javascript
function transformString() {
    const inputString = document.getElementById('stringInput').value;
    const length = inputString.length;
    let transformedString = '';

    if (length % 15 === 0) {
        // Reverse the string
        transformedString = inputString.split('').reverse().join('');
        // Replace each character with its ASCII code
        transformedString = transformedString.split('').map(char => char.charCodeAt(0)).join(' ');
    } else if (length % 3 === 0) {
        // Reverse the string
        transformedString = inputString.split('').reverse().join('');
    } else if (length % 5 === 0) {
        // Replace each character with its ASCII code
        transformedString = inputString.split('').map(char => char.charCodeAt(0)).join(' ');
    } else {
        transformedString = inputString;
    }

    document.getElementById('result').innerText = transformedString;
}
```

## Conclusion
The String Transformation Challenge applies specific transformations to a string based on its length. By entering a string and clicking "Transform," the appropriate transformation is displayed based on the rules provided. This solution uses HTML, CSS, and JavaScript, ensuring it runs efficiently within the browser.
