create a virtual environment 
```python
python -m venv venv
```
activate the virtual environment 
```python
venv\Scripts\activate
```
install django framework in the virtual environment 
```python
pip install django
```
```python
pip install Django==3.2.4
```
```python
django-admin startproject BlogProject .
```
```python
django-admin startapp BlogApp
```
```python
pip install mysqlclient
```
```python
pip install mysqlclient==1.3.6
```
```python
pip freeze > requirements.txt
```
```python
pip install -r requirements.txt
```
```python
pip uninstall -r requirements.txt
```
```python
pip uninstall -y -r requirements.txt
```
```python
deactivate
```
# Django API
```python
pip install djangorestframework
```
Add 'rest_framework' to your INSTALLED_APPS setting.
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```
  
# git commands 
  
```shell
echo "# Ridhun_Django_Blog_and_PSC" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/ridhun55/Ridhun_Django_Blog_and_PSC.git
git push -u origin main

```
