
# Create Venv for django
```shell
python -m venv venv
```
# Activate myenv 
```shell
venv\Script\activate
```
# Install Djnago
```shell
pip install django
```

# Create Django Project (API_Project)
```shell
django-admin startproject API_Project 
```
# Create Django App (API_APP)
```shell
django-admin startapp API_APP 
```
add API_APP into Settings.py
```shel
INSTALLED_APPS = [
    ...,
    'API_APP.apps.ApiAppConfig',
    ...,
]
```
# Install Django Rest Framework
```shell
pip install djangorestframework
```
# Add 'rest_framework' to your INSTALLED_APPS setting.
```
INSTALLED_APPS = [
    ...,
    "rest_framework",
    ...,
]
```
# Run Django Project
```shell
python manage.py runserver
```





======================================================

# Create Model (Task) in API_APP

```python
from django.db import models

class Task(models.Model):
   title = models.CharField(max_length=200)
   completed = models.BooleanField(default=False, blank=True, null=True)
   
   def __str__(self):
      return self.title

```

# migrate
```shell
python manage.py makemigrations
```
```shell
python manage.py migrate
```

# Add API_Project / urls.py

```shell
from django.contrib import admin
from django.urls import path,include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('API_APP.urls')),
]
```
# Add API_App / urls.py

```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
]

```

# 1. First Test API_App / View.py 
[http://127.0.0.1:8000/api/]
```shell
from django.shortcuts import render
from django.http import JsonResponse

def apiOverview(request):
   return JsonResponse("API overview page", safe=False)
```
# 2. Second Test API_App / View.py ( add 'api_view' decorator) 
[http://127.0.0.1:8000/api/]
```shell
from django.shortcuts import render
from django.http import JsonResponse

from rest_framework.decorators import api_view
from rest_framework.response import Response

@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)
 
```
============= serializers =============================

# 1. Add API_App / serializers.py
```python
from django.db import models
from django.db.models import fields
from rest_framework import serializers
from . models import Task

class TaskSerializer(serializers.ModelSerializer):
   class Meta:
      model = Task
      fields = '__all__'
```

# 2. write API_App / view.py for the 'taskList' 
```python
from django.shortcuts import render
from django.http import JsonResponse
from rest_framework import serializers

from rest_framework.decorators import api_view
from rest_framework.response import Response

from . models import Task
from . serializers import TaskSerializer


@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)


@api_view(['GET'])    
def taskList(request):
   task = Task.objects.all()
   serializer = TaskSerializer(task, many=True)
   return Response(serializer.data)
```

# 3. write API_App / urls.py for the 'taskList' 
[http://127.0.0.1:8000/api/task-list/]
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
    path('task-list/', views.taskList, name='task-list'),
]
```

# 4. write API_App / view.py for the 'taskDetail' 
```python
from django.shortcuts import render
from django.http import JsonResponse
from rest_framework import serializers

from rest_framework.decorators import api_view
from rest_framework.response import Response

from . models import Task
from . serializers import TaskSerializer


@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)


@api_view(['GET'])      
def taskList(request):
   task = Task.objects.all()
   serializer = TaskSerializer(task, many=True)
   return Response(serializer.data)


@api_view(['GET'])      
def taskDetail(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(task, many=False)
   return Response(serializer.data)
```

# 5. write API_App / urls.py for the 'taskDetail' 
[http://127.0.0.1:8000/api/task-detail/1/]
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
    path('task-list/', views.taskList, name='task-list'),
    path('task-detail/<str:pk>/', views.taskDetail, name='task-detail'),
]
```
# 6. write API_App / view.py for the 'taskCreate'
```shell
from django.shortcuts import render
from django.http import JsonResponse
from rest_framework import serializers

from rest_framework.decorators import api_view
from rest_framework.response import Response

from . models import Task
from . serializers import TaskSerializer


@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)


@api_view(['GET'])      
def taskList(request):
   task = Task.objects.all()
   serializer = TaskSerializer(task, many=True)
   return Response(serializer.data)


@api_view(['GET'])      
def taskDetail(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(task, many=False)
   return Response(serializer.data)


@api_view(['POST'])      
def taskCreate(request):
   serializer = TaskSerializer(data = request.data)
   if serializer.is_valid():
      serializer.save()
   return Response(serializer.data)
```
# 7. write API_App / urls.py for the 'taskCreate' 
[http://127.0.0.1:8000/api/task-create/]
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
    path('task-list/', views.taskList, name='task-list'),
    path('task-detail/<str:pk>/', views.taskDetail, name='task-detail'),
    path('task-create/', views.taskCreate, name='task-create'),
]
```
# 8. write API_App / view.py for the 'taskUpdate'
```shell
from django.shortcuts import render
from django.http import JsonResponse
from rest_framework import serializers

from rest_framework.decorators import api_view
from rest_framework.response import Response

from . models import Task
from . serializers import TaskSerializer


@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)


@api_view(['GET'])      
def taskList(request):
   task = Task.objects.all()
   serializer = TaskSerializer(task, many=True)
   return Response(serializer.data)


@api_view(['GET'])      
def taskDetail(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(task, many=False)
   return Response(serializer.data)


@api_view(['POST'])      
def taskCreate(request):
   serializer = TaskSerializer(data = request.data)
   if serializer.is_valid():
      serializer.save()
   return Response(serializer.data)


@api_view(['POST'])      
def taskUpdate(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(instance = task, data = request.data)
   if serializer.is_valid():
      serializer.save()
   return Response(serializer.data)
```
# 9. write API_App / urls.py for the 'taskUpdate' 
[http://127.0.0.1:8000/api/task-update/1]
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
    path('task-list/', views.taskList, name='task-list'),
    path('task-detail/<str:pk>/', views.taskDetail, name='task-detail'),
    path('task-create/', views.taskCreate, name='task-create'),
    path('task-update/<str:pk>/', views.taskUpdate, name='task-update'),
]
```
# 8. write API_App / view.py for the 'taskDelete'
```shell
from django.shortcuts import render
from django.http import JsonResponse
from rest_framework import serializers

from rest_framework.decorators import api_view
from rest_framework.response import Response

from . models import Task
from . serializers import TaskSerializer


@api_view(['GET'])
def apiOverview(request):
   api_test = {
      'name' : 'ridhun',
      'age' : 27,
      'class' : 'MSC',
   }
   return Response(api_test)


@api_view(['GET'])      
def taskList(request):
   task = Task.objects.all()
   serializer = TaskSerializer(task, many=True)
   return Response(serializer.data)


@api_view(['GET'])      
def taskDetail(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(task, many=False)
   return Response(serializer.data)


@api_view(['POST'])      
def taskCreate(request):
   serializer = TaskSerializer(data = request.data)
   if serializer.is_valid():
      serializer.save()
   return Response(serializer.data)


@api_view(['POST'])      
def taskUpdate(request, pk):
   task = Task.objects.get(id=pk)
   serializer = TaskSerializer(instance = task, data = request.data)
   if serializer.is_valid():
      serializer.save()
   return Response(serializer.data)


@api_view(['DELETE'])      
def taskDelete(request, pk):
   task = Task.objects.get(id=pk)
   task.delete()
   return Response("Deleted Successfully")
```
# 9. write API_App / urls.py for the 'taskDelete' 
[http://127.0.0.1:8000/api/task-delete/1]
```shell
from django.urls import path
from . import views

urlpatterns = [
    path('', views.apiOverview, name='api-overview'),
    path('task-list/', views.taskList, name='task-list'),
    path('task-detail/<str:pk>/', views.taskDetail, name='task-detail'),
    path('task-create/', views.taskCreate, name='task-create'),
    path('task-update/<str:pk>/', views.taskUpdate, name='task-update'),
    path('task-delete/<str:pk>/', views.taskDelete, name='task-delete'),
]
```

# All Links
```shell
task-list/
task-detail/2
task-create/
task-update/1
task-delete/2
```
