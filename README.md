# Projects Overview

This repository contains a collection of web development projects that showcase various interactive and dynamic features using HTML, CSS, and JavaScript. Each project is designed to be responsive, ensuring a seamless user experience across different devices, including desktops, tablets, and mobile devices. Below is a detailed description of each project, including features and usage instructions.

## Table of Contents
1. [Interactive Photo Gallery](#interactive-photo-gallery)
2. [String Transformation Challenge](#string-transformation-challenge)
3. [Gallery with Panels](#gallery-with-panels)
4. [Array Manipulation](#array-manipulation)

## Interactive Photo Gallery

### Overview
The Interactive Photo Gallery project aims to create a dynamic gallery based on provided Figma designs. The gallery is responsive and includes features such as image thumbnail navigation, full-size image viewing, and specified interactions.

### Features
- **Responsive Design:** Works seamlessly on desktop, tablet, and mobile devices.
- **Thumbnail Navigation:** Allows users to navigate through images using thumbnails.
- **Full-size Image Viewing:** Displays images in full size when a thumbnail is clicked.
- **Interactive Elements:** Includes interactions specified in the Figma designs.

### Usage
#### Installation
No installation is required. Simply open the `index.html` file in a web browser.

#### Code

##### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Interactive Photo Gallery</title>
</head>
<body>
    <div class="gallery-container">
        <div class="thumbnail-container">
            <img src="image1-thumb.jpg" alt="Thumbnail 1" class="thumbnail" onclick="showImage('image1.jpg')">
            <img src="image2-thumb.jpg" alt="Thumbnail 2" class="thumbnail" onclick="showImage('image2.jpg')">
            <img src="image3-thumb.jpg" alt="Thumbnail 3" class="thumbnail" onclick="showImage('image3.jpg')">
            <!-- Add more thumbnails as needed -->
        </div>
        <div class="fullsize-image-container">
            <img src="image1.jpg" alt="Full-size" id="fullsizeImage">
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

##### CSS
```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.gallery-container {
    text-align: center;
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 90%;
    max-width: 1200px;
}

.thumbnail-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 20px;
}

.thumbnail {
    width: 100px;
    height: 100px;
    margin: 5px;
    cursor: pointer;
    transition: transform 0.3s;
}

.thumbnail:hover {
    transform: scale(1.1);
}

.fullsize-image-container {
    display: flex;
    justify-content: center;
}

#fullsizeImage {
    max-width: 100%;
    max-height: 500px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
    .thumbnail {
        width: 80px;
        height: 80px;
    }
    
    #fullsizeImage {
        max-height: 300px;
    }
}

@media (max-width: 480px) {
    .thumbnail {
        width: 60px;
        height: 60px;
    }
    
    #fullsizeImage {
        max-height: 200px;
    }
}
```

##### JavaScript
```javascript
function showImage(imageSrc) {
    const fullsizeImage = document.getElementById('fullsizeImage');
    fullsizeImage.src = imageSrc;

    // Add a fade-in effect
    fullsizeImage.classList.remove('fade-in');
    void fullsizeImage.offsetWidth; // Trigger reflow
    fullsizeImage.classList.add('fade-in');
}

// Ensure fade-in effect is defined in CSS
document.addEventListener('DOMContentLoaded', () => {
    const style = document.createElement('style');
    style.innerHTML = `
        .fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    `;
    document.head.appendChild(style);
});
```

## String Transformation Challenge

### Overview
This project transforms a given string based on its length using specified rules. The transformation rules depend on the divisibility of the string length by 3, 5, and 15.

### Features
- **Reverse String:** If the length is divisible by 3.
- **ASCII Code Replacement:** If the length is divisible by 5.
- **Combined Transformation:** If the length is divisible by 15.

### Usage
#### Installation
No installation is required. Simply open the `index.html` file in a web browser.

#### Code

##### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>String Transformation Challenge</title>
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

##### CSS
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

##### JavaScript
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

## Gallery with Panels

### Overview
This project is an interactive photo gallery that showcases different animals with their respective locations. The gallery is designed to be responsive, ensuring a seamless experience on desktop, tablet, and mobile devices.

### Features
- **Responsive Design:** Works seamlessly on desktop, tablet, and mobile devices.
- **Interactive Panels:** Each panel displays an image, a title, location, and a link to know more.
- **Smooth Transitions:** Includes CSS transitions for a smooth user experience.

### Usage
#### Installation
No installation is required. Simply open the `index.html` file in a web browser.

#### Code

##### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Gallery</title>
</head>
<body>
    <div class="container">
        <div class="panel" style="background-image:url('fox.jpg')">
            <div

 class="text">
                <h1>FENNEC FOX</h1><br>
                <p>India</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('whale.avif')">
            <div class="text">
                <h1>HUMPBACK WHALE</h1><br>
                <p>South Africa</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('baboon.jpg')">
            <div class="text">
                <h1>COMMON BROWN BABOON</h1>
                <p>South Africa</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('deer.webp')">
            <div class="text">
                <h1>SPOTTED DEER</h1>
                <p>Amazon</p> 
                <a href="#" class="more">Know more &rarr;</a>
            </div>
        </div>
    </div>
    <script src="gallery.js"></script>
</body>
</html>
```

##### CSS
```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;
    max-width: 1200px;
}

.panel {
    position: relative;
    flex: 1 1 calc(50% - 10px);
    margin: 5px;
    height: 200px;
    background-size: cover;
    background-position: center;
    border-radius: 10px;
    transition: transform 0.3s, box-shadow 0.3s;
}

.panel:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.text {
    position: absolute;
    bottom: 10px;
    left: 10px;
    color: white;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.6);
}

.text h1 {
    margin: 0;
    font-size: 1.5em;
}

.text p {
    margin: 5px 0;
}

.text .more {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

@media (max-width: 768px) {
    .panel {
        flex: 1 1 calc(100% - 10px);
        height: 150px;
    }

    .text h1 {
        font-size: 1.2em;
    }
}

@media (max-width: 480px) {
    .panel {
        height: 120px;
    }

    .text h1 {
        font-size: 1em;
    }
}
```

##### JavaScript
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const panels = document.querySelectorAll('.panel');

    panels.forEach(panel => {
        panel.addEventListener('click', () => {
            panels.forEach(p => p.classList.remove('active'));
            panel.classList.add('active');
        });
    });
});
```

## Array Manipulation

### Overview
This project provides a solution for checking if there exists a contiguous subarray within an array that sums up to a given target sum. The implementation is efficient, with a time complexity of O(n).

### Features
- **Efficient Subarray Sum Check:** Uses a sliding window technique to check for a contiguous subarray with a given sum.
- **Responsive Design:** Works seamlessly on desktop, tablet, and mobile devices.

### Usage
#### Installation
No installation is required. Simply open the `index.html` file in a web browser.

#### Code

##### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>Array Manipulation</title>
</head>
<body>
    <div class="container">
        <h1>Array Subarray Sum Check</h1>
        <input type="text" id="arrayInput" placeholder="Enter array elements separated by commas">
        <input type="number" id="targetInput" placeholder="Enter target sum">
        <button onclick="checkSubarraySum()">Check</button>
        <p id="result"></p>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

##### CSS
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

##### JavaScript
```javascript
function checkSubarraySum() {
    const arrayInput = document.getElementById('arrayInput').value;
    const targetSum = parseInt(document.getElementById('targetInput').value);
    const arr = arrayInput.split(',').map(Number);
    let start = 0, currentSum = 0;

    for (let end = 0; end < arr.length; end++) {
        currentSum += arr[end];

        while (currentSum > targetSum) {
            currentSum -= arr[start++];
        }

        if (currentSum === targetSum) {
            document.getElementById('result').innerText = `True: Subarray exists from index ${start} to ${end}`;
            return;
        }
    }

    document.getElementById('result').innerText = 'False: No such subarray exists';
}
```

This README.md file provides an overview and instructions for each project included in this repository. Each project demonstrates different aspects of web development, including responsive design, interactive elements, and efficient algorithms.
