## Django Apps
Consider Django apps as the build in components. Or pieces of a bigger Django project.
There are some apps which is installed as default.

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]
```
Once you creating the superuser and then we will get the access to the admin. There are many option in the admin . page like how to created a new user and edit the username and password.

## Custom app component 

Purpose of Django is to make custom apps

`python manage.py startapp newone` 

## about models.py
 Assume that you have a product and you have to create a memmory about the product
   If there is a attribute inorder to map it to the database `attribute = model.Textfield()`. Then add the field to the Installed app. Then make the migrations.
   
 Once the model is created then and add this to the admin page. Open the admin page and then import model file and then  import the function defined in the model file then register it `admin.site.register(product)` after that check the admin page you can see the the model that you created and you can add the as much as product you want and for each product we have defined some field in the function definition all the attribite will be the char of the product that we are creating and you can add the fields as you want.

## Django shell
Open the terminal and go to the folder where the manage.py is there and in that run the command `python manage.py shell` which open a django shell.
We can  do relative imports in the shell 
run `python manage.py shell` . In the above case we created a app then we added some models with some featues 
