# Setting up PostgreSQL in Django 

# Install psycopy2 package

```shell
pip install psycopg2
```

# Settings

```python
DATABASES = {
   'default': {
       'ENGINE': 'django.db.backends.postgresql',
       'NAME': ‘<database_name>’,
       'USER': '<database_username>',
       'PASSWORD': '<password>',
       'HOST': '<database_hostname_or_ip>',
       'PORT': '<database_port>',
   }
}
```
# Example

```python
DATABASES = {
   'default': {
       'ENGINE': 'django.db.backends.postgresql',
       'NAME': 'blogDB',
       'USER': 'postgres',
       'PASSWORD': 'silicon',
       'HOST': 'localhost',
       'PORT': '5432',
   }
}
```

# Migarte

```shell
python manage.py makemigrations
```
```shell
python manage.py migrate
```
```shell
python manage.py createsuperuser
```
