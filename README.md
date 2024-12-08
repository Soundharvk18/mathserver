# Ex.05 Design a Website for Server Side Processing
# Date:30/11/24
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
math.html
{%load static%}

<!DOCTYPE html>
<html lang="en">
<head>

    <title>Lamp Filament Power Calculator</title>
    <style>
        body {
            font-family:Arial, Helvetica, sans-serif;
            margin: 20px;
            background-color: skyblue;
        }
        .container {
            margin-top: 18%;
            max-width: 550px;
            background-color: whitesmoke ;
            height: 300px;
            margin-left: 33%;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px red;
        }
        .container h1 {
            text-align: center;
            color: #333;
        }
        .form-group {
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #555;
        }
        .form-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e7f5e1;
            border: 1px solid #c3e6cb;
            border-radius: 5px;
            text-align: center;
            color: #155724;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 >Power Calculator</h1>

        <div class="form-group">
            <form method="POST">
                {% csrf_token %}
            
                <label name='intensity' for="INTENSITY">INTENSITY</label>
                <input type="text" name='intensity' placeholder="Enter intensity" id="intensity" value="{{i}}"> <br>
        
             
           <label name="resistance" for="RESISTANCE" id="res">RESISTANCE</label>
                <input type="text " name="resistance" placeholder="Enter resistance" id="resistance" value="{{r}}"> <br>
         
            <button type="submit">Calculate Power</button> <br>
            <label name="power" for="POWER">POWER</label>

            <input type="text" placeholder="Answer" id="power" name="power" value="{{power}}" readonly>

        </div>
        
        
    </div>

    
</body>
</html>

urls.py
from django.contrib import admin 
from django.urls import path 
from server import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerlamp/',views.powerlamp,name="powerlamp"),
    path('',views.powerlamp,name="powerlamproot")
]

views.py

from django.shortcuts import render
def powerlamp(request): 
    context={} 
    context['power']="0" 
    context['i']="0" 
    context['r']="0" 
    if request.method=='POST': 
        print("POST method is used")
        i=request.POST.get('intensity','0')
        r=request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power=(int(i) ** 2 ) * int(r) 
        context['power']=power
        context['i']=i
        context['r']=r 
        print('Power=',power) 
    return render(request,'math.html',context)
```


# SERVER SIDE PROCESSING:
![Screenshot 2024-12-08 222403](https://github.com/user-attachments/assets/e8a8ffa4-6631-4b73-8f23-ae158d157861)
![Screenshot 2024-12-08 222414](https://github.com/user-attachments/assets/ce9f330b-e8ff-48c6-b8ac-a4fbab1d39ea)

# HOMEPAGE:
![Screenshot 2024-12-08 223929](https://github.com/user-attachments/assets/55e855e1-1536-42e9-94d9-b0b9d171f4b9)

# RESULT:
The program for performing server side processing is completed successfully.
