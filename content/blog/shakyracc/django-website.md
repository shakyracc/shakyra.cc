title: Setting Up A Django Project
date: 2022-07-26
tags: pelican
slug: setting-up-django-project

## Environment Set Up
1. Create new directory for project to live in 

mkdir django-website 
cd djangor-website

2. Create virtual environment

python3 -m venv django_website

3. Activate virtual environment
 
source venv/bin/activate

4. Install Django into new virtual environment 

(venv) $ pip install Django

## Create a Django Project

1. Ensure you are in the django_website directory and activated virtual environment 

2. Creathe the project 

$ django-admin startproject personal_portfolio

3. Reorder directory 

$ mv personal_portfolio/manage.py ./
$ mv personal_portfolio/personal_portfolio/* personal_portfolio
$ rm -r personal_portfolio/personal_portfolio/

4. Start the server to check the set up was successful 

$ python manage.py runserver

5. Go to localhost:8000 in browser. should see "istall worked successfully" page

## Create a Django Application 

1. Create the app

$ python manage.py startapp hello_world

2. Install the app in the personal_portfolio project.

In django-website/personal_portfolio/settings.py add the following line of code under INSTALLED_APPS:

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'hello_world',
]

## Create a View 

1. open views.py from the hello_world directory and define the view function called hello_world() by adding
 the following 

from django.shortcuts import render

def hello_world(request):
    return render(request, 'hello_world.html', {})
    
2. Make template directory and add HTML template

$ mkdir hello_world/templates/
$ touch hello_world/templates/hello_world.html

3. Add the following lines of HTML to the file 

`<h1>Hello, World!</h1>`

4. Inside personal_portfolio/urls.py add URL configuration for the hello_worl app

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('hello_world.urls')),
]

5. Create urls.py module inside the hello_world application 

$ touch hello_world/urls.py

6. Import path object and app's views module. Create list of URL patterns that correspond ti the various view functions

from django.urls import path
from hello_world import views

urlpatterns = [
    path('', views.hello_world, name='hello_world'),
]

# ⚠️ Article to be completed soon 






