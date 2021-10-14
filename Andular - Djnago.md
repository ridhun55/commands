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
add it to your installed apps & middleware class
```
INSTALLED_APPS = [
    ...,
    "corsheaders",
    ...,
]

MIDDLEWARE = [
    ...,
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
    ...,
]
```
