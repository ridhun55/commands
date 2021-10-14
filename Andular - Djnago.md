#Install the Angular CLI
```shell
npm install -g @angular/cli
```
# Version
```shell
ng --version
```
# Create Venv for django
```shell
python -m venv myenv
```
# Activate myenv 
```shell
myenv\Script\activate
```
# Install Djnago
```shell
pip install django
```
# Install Django Rest Framework
```shell
pip install djangorestframework
```
# Create Django Project
```shell
django-admin startproject DjangoAPI 
```
```shell
cd DjangoAPI 
```
```shell
code . 
```
# Run Django Project
```shell
python manage.py runserver
```
# Install Django Core Header Package
```shell
pip install django-cors-headers
```
add it to your installed apps, CORS_ORIGIN_ALLOW_ALL & middleware class 
```
INSTALLED_APPS = [
    ...,
    "corsheaders",
    ...,
]

CORS_ORIGIN_ALLOW_ALL = True

MIDDLEWARE = [
    ...,
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
    ...,
]
```

# Create Django App
```shell
python manage.py startapp EmployeeApp
```

# Register EmployeeApp in Settings.py
```
INSTALLED_APPS = [
    ...,
    "EmployeeApp.apps.EmployeeappConfig",
    ...,
]
```

# Register Rest Framework in Settings.py
```
INSTALLED_APPS = [
    ...,
    "rest_framework",
    ...,
]
```

======================================================

# Create Model in EmployeeApp/models.py

```python
from django.db import models

class Departments(models.Model):
   DepartmentId = models.AutoField(primary_key=True)
   DepartmentName = models.CharField(max_length=100)
    
class Employees(models.Model):
   EmployeeId = models.AutoField(primary_key=True)
   EmployeeName = models.CharField(max_length=100)
   Department = models.CharField(max_length=100)
   DateOfJoining = models.DateField()
   PhotoFileName = models.CharField(max_length=100)
```

# migrate
```shell
python manage.py makemigrations
```
```shell
python manage.py migrate
```

# Add EmployeeApp / urls.py

```shell
from django.conf.urls import url
from EmployeeApp import views

urlpatterns[
   url(r'^department/$',views.departmentApi),
   url(r'^department/([0-9]+)$',views.departmentApi)
]
```

# Include it into main urls.py
```shell

from django.contrib import admin
from django.urls import path,include
from django.conf.urls import url

import EmployeeApp

urlpatterns = [
    path('admin/', admin.site.urls),
    url(r'^',include('EmployeeApp.urls'))
]

```

# Add serializer
1. add a file in EmployeeApp / serializers.py 

```python
from rest_framework import serializers
from EmployeeApp.models import Departments,Employees

class DepartmentSerializer(serializers.ModelSerializer):
   class meta:
      model = Departments
      fields = ('DepartmentId',
               'DepartmentName')
      
class EmployeeSerializer(serializers.ModelSerializer):
   class meta:
      model = Employees
      fields = ('EmployeeId', 
               'EmployeeName', 
               'Department', 
               'DateOfJoining', 
               'PhotoFileName')
```

2.write view.py for api for GET,POST,PUT,DELETE
```python
from django.shortcuts import render
from django.views.decorators.csrf import csrf_exempt
from rest_framework.parsers import JSONParser
from EmployeeApp.models import Departments,Employees
from EmployeeApp.serializers import DepartmentSerializer,EmployeeSerializer
from django.http.response import JsonResponse


@csrf_exempt
def DepartmentApi(request,id=0):
   if request.method == 'GET':
      departments = Departments.objects.all()
      departments_serializer = DepartmentSerializer(departments, many=True)
      return JsonResponse(departments_serializer.data,safe=False)
   
   elif request.method=='POST':
      department_data = JSONParser().parse(request)
      department_serializer = DepartmentSerializer(data=department_data)
      if department_serializer.is_valid():
         department_serializer.save()
         return JsonResponse("Add Successfully!!", safe=False)
      return JsonResponse("Faild to Add", safe=False)
   
   elif request.method=='PUT':
      department_data = JSONParser().parse(request)
      department = Departments.objects.get(DepartmentId = department_data['DepartmentId'])
      department_serializer = DepartmentSerializer(department, data = department_data)
      if department_serializer.is_valid():
         department_serializer.save()
         return JsonResponse("Updated Successfully!!", safe=False)
      return JsonResponse("Faild to Update", safe=False)
   
   elif request.method=='DELETE':
      department = Departments.objects.get(DepartmentId = id)
      department.delete()
      return JsonResponse("Deleted Successfully!!", safe=False)
     
```
3. Run DjangoApp 
```shell
python manage.py runserver
```
4. Copy Localhost link
5. Open POSTMAN SOFTWARE



