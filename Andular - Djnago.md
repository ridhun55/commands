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

2.write view.py for api



