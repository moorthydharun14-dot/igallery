# Ex.08 Design of Interactive Image Gallery
## Date: 16.10.2025

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```py
projects's urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',include('gallery.urls')),
]

app's urls.py

from django.urls import path
from . import views

urlpatterns = [
    path('',views.index,name='index'),
]

views.py 

from django.shortcuts import render

def index(request):
    return render(request,'gallery/index.html')
```
```html
<!-- Photo Gallery Template -->
 {% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Stars Properties Photo Gallery</title>
    <link rel="stylesheet" href="{% static 'gallery/style.css' %}">
    
</head>
<body img="{% static 'gallery/images/collapse.jpg' %}">
    <h1>Stars Properties Photo Gallery</h1>

    <div class="gallery">
        <img src="{% static 'gallery/images/star factory(milkyway).jpg' %}" alt="Photo 1">
        <img src="{% static 'gallery/images/stellar kinamatics.jpg' %}" alt="Photo 2">
        <img src="{% static 'gallery/images/stellar magnetic field.jpg' %}" alt="Photo 3">
        <img src="{% static 'gallery/images/stellar mass.jpg' %}" alt="Photo 4">
        <img src="{% static 'gallery/images/stellar radiation.jpg' %}" alt="Photo 5">
        <img src="{% static 'gallery/images/collapse.jpg' %}" alt="Photo 6">
    </div>

    <div id="modal" class="modal">
        <span class="close">&times;</span>
        <img class="modal-content" id="modalImage">
    </div>

    <script src="{% static 'gallery/script.js' %}"></script>
</body>
</html>
```
```css
/* CSS file */
body {
    text-align: center;
    color: aliceblue;
    background-color: black;
    font-family: Arial, sans-serif;
    height: 100vh;
}

.gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    margin-top: 30px;
    height: 600px;
}

.gallery img {
    width: 200px;
    height: 150px;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.3s;
    height: 350px;
    width: 430px;
}

.gallery img:hover {
    transform: scale(1.1);
}

/* Modal styles */
.modal {
    display: none;
    position: fixed;
    z-index: 2;
    padding-top: 80px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.8);
}

.modal-content {
    margin: auto;
    display: block;
    width: 60%;
    border-radius: 10px;
}

.close {
    position: absolute;
    top: 30px;
    right: 50px;
    color: white;
    font-size: 40px;
    cursor: pointer;
}
```
```js
// JS file
// Get modal elements
var modal = document.getElementById("modal");
var modalImg = document.getElementById("modalImage");
var closeBtn = document.getElementsByClassName("close")[0];

// Open image in modal when clicked
document.querySelectorAll(".gallery img").forEach(img => {
    img.addEventListener("click", () => {
        modal.style.display = "block";
        modalImg.src = img.src;
    });
});

// Close modal on click
closeBtn.onclick = function() {
    modal.style.display = "none";
};

// Close modal when clicking outside image
modal.onclick = function(e) {
    if (e.target === modal) {
        modal.style.display = "none";
    }
};
```

## OUTPUT:
![alt text](<Screenshot 2025-10-14 231920.png>)
## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
