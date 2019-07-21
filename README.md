# Django_basics

Reqiuremnets:

1. phython
2.Django



## How to start a Django project

Make sure that you have installed the proper Django version. Select the folder where you want to start the Django project and in terminal type `django-admin startproject mysite .`

Here django-admin.py is the script is running and which results in producung necessary files and dorectories for our project

These are some files which are generated when django-admin.py started
1.manage.py : helps in the management of the files
2.settigs.py : helps in configuration of the website
3.url.py  : is the url resolver

first of all need to chanke some configuratiom in the settings.py like the time zone and language.

Then add a path to static files.Using the commands `STATIC_ROOT = os.path.join(BASE_DIR, 'static')`

Since we are using pythonanywhere as our server and if we simply kept the ALLOWED_HOSTS empty it will call against the local host so set it to `ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']`

### Setting up a database 
There are many database available and sqlite3 is the default one and we are it.

so don't have to change the code and now in terminal run manage.py `python manage.py merge`


### Web server

Run the code in terminal `python manage.py runserver`

###Django models

Its nothing but the oops concepts in creating blog models
Inorder to create a blog we have to model a blog post then and the blog post should have some properties(models are nothing but oblect in oops concepts with properties and methods).

But Django models are special type of models where they are saved in the database. Here sqlite is the database that we are using.

for the first step is creating an application.

It makes everything well organised.
for that run the following command in the terminal. `python manage.py startapp blog`
So the blog is created so we have to add the infomation about the app (the blog that we just created) in the settings file.

The all model need for our blog have to be added to the models.py in blog

When we creating a model that is nothing but a class we will pass a parameter to class definition (models.Model) which indicated its a Django model and django will understand that this should be saved in the database

### Create tables for your models in the database 

That simply means add the models to the database.
 by running the code `python manage.py makemigrations blog` will make django undertand that there are some changes in the blog
 
 Then follow the code to run the blog `python manage.py migrate blog`
