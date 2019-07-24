# Django_basics

Requirements:

1. python
2.Django



## How to start a Django project

Make sure that you have installed the proper Django version. Select the folder where you want to start the Django project and in terminal type `django-admin startproject mysite .`

Here django-admin.py is the script is running and which results in producing necessary files and directories for our project

These are some files which are generated when django-admin.py started
1.manage.py : helps in the management of the files
2.settigs.py : helps in the configuration of the website
3.url.py: is the URL resolver

first of all, we need to change some configuration in the settings.py like the time zone and language.

Then add a path to static files.Using the commands `STATIC_ROOT = os.path.join(BASE_DIR, 'static')`

Since we are using pythonanywhere as our server and if we simply kept the ALLOWED_HOSTS empty it will call against the localhost so set it to `ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']`

### Setting up a database 
There are many databases available and sqlite3 is the default one and we are it.

so don't have to change the code and now in terminal run manage.py `python manage.py merge`


### Webserver

Run the code in terminal `python manage.py runserver` . So you can see the website running in the browser.

### Django models

Its nothing but the oops concepts in creating blog models
In order to create a blog we have to model a blog post then and the blog post should have some properties(models are nothing but object in oops concepts with properties and methods).

But Django models are a special type of model where they are saved in the database. Here SQLite is the database that we are using.

the first step is creating an application. It makes everything little tidy.

It makes everything well organized.
for that run the following command in the terminal. `python manage.py startapp blog`
So the blog is created so we have to add the information about the app (the blog that we just created) in the settings file.
Once the app is created we  have to inform Django that it should use it by adding the app name in the **INSTALLED_APP** list.

The all model(the objects of the app) need for our blog has to be added to the models.py.

When we creating a model that is nothing but a class we will pass a parameter to class definition (models.Model) which indicated its a Django model and Django will understand that this should be saved in the database

It will have 

### Create tables for your models in the database 

That simply means add the models to the database.
 by running the code `python manage.py makemigrations blog` will make Django understand that there are some changes in the blog
 
 Then follow the code to run the blog `python manage.py migrate blog` --> it will  ultimately add the model to the database.
 
 ### Django admin
 
 
 To add, edit and delete the post that we have modeled.
 
 In the admin.py add line `admin.site.register(Post)` and don't forget to import the Post model that we defined earlier using `from .models import Post` . To make our model visible on the admin page we have to register it.
 
 Now run the server `python manage.py runserver` 
 
  Type the following command in the browser http://127.0.0.1:8000/admin/ and you can see a login page but in order to login, you may need to create an account in the superuser 
  
  In order to create the account in superuser run the following commands `python manage.py createsuperuser`
  
  Once the account is created login to the admin  page and login
Yes! The admin page is ready you can add the text field and give a post name etc. Set at least two of the post with published date and not all which will help later.

##Depoly
Deploying is the process of publishing the application on the internet and everyone will be able to see it. As we know the website has to sit on a server and we are using the *pythonanywhere* for the website which doesn't have too many users it's free.

**Setting up our blog on pythonanywhere**
Pythonanywhere is a service for running python code on servers. Once an API token is created can configure the site on pythonanywhere dashboard. Click on the bash tab which will open a bash terminal.
confirm that pythonanywhere is installed in the  (If not run this command in the environment`pip3 install --user pythonanywhere`).

Then run the command `$ pa_autoconfigure_django.py https://github.com/<your-github-username>/<repo name>`

After running the command you can see that the git hub is getting downloaded 
Then create a virtual environment in python anywhere. Then update the settings file with some deployment settings. setting up a database in pythonanywhere using `manage.py migrate` setting up the static files and configuring the python anywhere to serve the web app.

So the one thing is to keep in mind is that the database of the local and the database of the python anywhere is two entirely different things so we can create two separate admin pages for both and manage them separately.

Once you have done this you can run the server and you can understand that its same as the running in the local machine but now it's running on the server :)

### Django URL

Ever page on internet need an URL. There is something called URLconf is a set of patterns where the Django try to  match
the requested URL to find the correct view.

Now we can create our own URL. along with the path from django.urls add include also then insert a line like `path('',include(blog.urls))` . Now Django will redirect everything from 'http://127.0.0.1:8000/'  to blog.urls and looks for the further instructions there.

Now create a empty file named url.py in blogs folder. Add these two lines `from django.urls import path` and`from . import views ` and then ` urlpatterns = [path ('',view.post_list , name = 'post_list'),]` .Now we are assigning a view called post_list to URL .URL pattern will match the empty string and ignore the domain name .In simpler words This  pattern tells Django that view.post_list is the right place to go if someone enters the web address as http:// 120.0.0.1:8000/ the name part that defines in the URL pattern is the name that used to identify the view.

we are not done yet. View is the place where we put logics for our application. Open blogs/views.py its just a pytho file were we create a definition for our post_list.
Import following `from django.shortcuts import render` then add the definition as 
`def post_list(request):
       return render(request,'blog/post_list.html',{} )`
       
 But there is no html page there so create `blog/templates/blog` directories and then create `post_list.html` inside that.
 
 Add the html scripts as 
 ```<html>
    <body>
        <p>Hi there</p>
        <p>It works</p>
    </body>
</html>```
