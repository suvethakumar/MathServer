# Ex.05 Design a Website for Server Side Processing
## Date:1/10/25

## AIM:
 To design a website to calculate the Body Mass Index in the server side.


## FORMULA:
BMI = W/(H/100**2)
<br> BMI --> Body Mass Index
<br> W --> Weight
<br> H --> Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

```
math.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>BMI Calculator</h1>
        <form>
            <label for="weight">Weight (kg):</label>
            <input type="number" id="weight" required>
            <label for="height">Height (m):</label>
            <input type="number" id="height" required>
            <button id="calculate-btn">Calculate BMI</button>
        </form>
        <p id="result"></p>
    </div>

    <script src="script.js"></script>
</body>
</html>

  
    

views.py

from django.shortcuts import render
def bmi(request):
    context={}
    context['bmi'] = "0"
    context['w'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        w = request.POST.get('Weight','w')
        h = request.POST.get('Height','h')
        print('request=',request)
        print('Weight=',w)
        print('Height=',h)
        a = int(w)
        b = int(h)
        bmi = a/(b*b)
        context['bmi'] = bmi
        context['w'] = w
        context['h'] = h
        print('BMI=',bmi)
    return render(request,'mathapp/math.html',context)

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('bodymassindex',views.bmi,name="bodymassindex"),
    path('',views.bmi,name="bodymassindexroot")
]

```


## SERVER SIDE PROCESSING:
![alt text](suve1.png)



## HOMEPAGE:

![alt text](<Screenshot (34).png>)



## RESULT:
The program for performing server side processing is completed successfully.
