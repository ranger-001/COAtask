# Interactive Photo Gallery

## Overview
This project aims to create an interactive photo gallery based on provided Figma designs. The gallery is responsive, ensuring a seamless user experience on desktop, tablet, and mobile devices. Features include image thumbnail navigation, full-size image viewing, and interactions specified in the designs.

## Features
- **Responsive Design:** Works seamlessly on desktop, tablet, and mobile devices.
- **Thumbnail Navigation:** Allows users to navigate through images using thumbnails.
- **Full-size Image Viewing:** Displays images in full size when a thumbnail is clicked.
- **Interactive Elements:** Includes interactions specified in the Figma designs.

## Usage
### Installation
No installation is required. Simply open the `index.html` file in a web browser.

### Code

#### HTML
# Interactive Photo Gallery

## Overview
This project aims to create an interactive photo gallery based on provided Figma designs. The gallery is responsive, ensuring a seamless user experience on desktop, tablet, and mobile devices. Features include image thumbnail navigation, full-size image viewing, and interactions specified in the designs.

## Features
- **Responsive Design:** Works seamlessly on desktop, tablet, and mobile devices.
- **Thumbnail Navigation:** Allows users to navigate through images using thumbnails.
- **Full-size Image Viewing:** Displays images in full size when a thumbnail is clicked.
- **Interactive Elements:** Includes interactions specified in the Figma designs.

## Usage
### Installation
No installation is required. Simply open the `index.html` file in a web browser.

### Code

#### HTML
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
            <div class="text">
                <h1>FENNEC <br>FOX</h1><br>
                <p>India</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('whale.avif')">
            <div class="text">
                <h1>HUMPBACK<br>WHALE</h1><br>
                <p>South Africa</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('baboon.jpg')">
            <div class="text">
                <h1>COMMON BROWN<br>BABOON</h1>
                <p>South Africa</p>
                <a href="#" class="more">know more &rarr;</a>
            </div>
        </div>
        <div class="panel" style="background-image:url('deer.webp')">
            <div class="text">
                <h1>SPOTTED<br>DEER</h1>
                <p>Amazon</p> 
                <a href="#" class="more">Know more &rarr;</a>
            </div>
        </div>
    </div>
    <script src="gallery.js"></script>
</body>

</html>
```

#### CSS
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4f4f9;
}

.container {
    display: flex;
    flex-wrap: wrap;
    width: 90%;
    max-width: 1200px;
}

.panel {
    flex: 1 1 calc(50% - 20px);
    margin: 10px;
    background-size: cover;
    background-position: center;
    position: relative;
    border-radius: 10px;
    overflow: hidden;
    transition: transform 0.3s, flex 0.3s;
}

.panel:hover {
    transform: scale(1.05);
    flex: 1 1 100%;
}

.text {
    position: absolute;
    bottom: 20px;
    left: 20px;
    color: white;
    background-color: rgba(0, 0, 0, 0.5);
    padding: 10px;
    border-radius: 5px;
}

.text h1 {
    font-size: 1.5rem;
    margin-bottom: 10px;
}

.text p {
    font-size: 1rem;
    margin-bottom: 10px;
}

.more {
    color: #ffd700;
    text-decoration: none;
    font-size: 1rem;
}

.more:hover {
    text-decoration: underline;
}

@media (max-width: 768px) {
    .panel {
        flex: 1 1 100%;
    }

    .text h1 {
        font-size: 1.2rem;
    }

    .text p, .more {
        font-size: 0.9rem;
    }
}


#### JavaScript
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

## Conclusion
The Interactive Photo Gallery provides a user-friendly interface for viewing images. By following the provided Figma designs, the gallery ensures a seamless experience on desktop, tablet, and mobile devices. The gallery features thumbnail navigation, full-size image viewing, and specified interactions, implemented using HTML, CSS, and JavaScript. Simply open the `index.html` file in a web browser to use the gallery.
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

#### JavaScript
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

## Conclusion
The Interactive Photo Gallery provides a user-friendly interface for viewing images. By following the provided Figma designs, the gallery ensures a seamless experience on desktop, tablet, and mobile devices. The gallery features thumbnail navigation, full-size image viewing, and specified interactions, implemented using HTML, CSS, and JavaScript. Simply open the `index.html` file in a web browser to use the gallery.
