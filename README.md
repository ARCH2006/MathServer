# Ex.05 Design a Website for Server Side Processing
## Date: 3.11.23

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
<html>
    <head>
        
        <Title>Calculate area of rectangle</Title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <style>
        body{background-color: violet;
        }
        .edge{
            width:1080px;
            margin-left:auto;
            margin-right: auto;
            padding-top: 200px;
            padding-left: 300px;
        }
        .box{
            align: center;
            display: block;
            border: darkslateblue;
            width:500px;
            min-height: 300px;
            font-size: 20px;
            background-color:cyan;
            text-align:center;
            margin-left:auto;
            margin-right: auto;
        }
        .formelt{
            color:red;
            text-align: center;
            margin-top: 5px;
            margin-bottom: 5px;
        }
        .h1{
            color:red;
            text-align: center;
            padding-top: 20px;
        }

        </style>

    </head>
    <body>
        <div class="edge">
            <div class="box">
                <h1>Area of Rectangle</h1>
                <form method="POST">
                {% csrf_token%}
                <div class="formelt">
                    Length: <input type="text" name="length" value="{{l}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    Breadth: <input type="text" name="breadth" value="{{b}}"></input>(in m)<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"></input><br/>
                </div>
                <div class="formelt">
                    Area: <input type="text" name="area" value="{{area}}"></input>m<sup>2</sup><br/>
                </div>
                </form>
            </div>

        </div>

   </body>
</html>

views.py
from django.shortcuts import render
def rectarea(request):
    context={}
    context['area'] = "0"
    context['l'] = "0"
    context['b'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        l = request.POST.get('length','0')
        b = request.POST.get('breadth','0')
        print('request=',request)
        print('Length=',l)
        print('Breadth=',b)
        area = int(l) * int(b)
        context['area'] = area
        context['l'] = l
        context['b'] = b
        print('Area=',area)
    return render(request,'mathapp/math.html',context)
        

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('areaofrectangle/',views.rectarea,name='areaofrectangle'),
    path('',views.rectarea,name="areaofrectangleroot")
]


```
## SERVER SIDE PROCESSING:
![Alt text](<Screenshot 2024-01-02 155929.png>)



## HOMEPAGE:
![Alt text](<Screenshot 2024-01-02 155804.png>)

## RESULT:
The program for performing server side processing is completed successfully.
