**How Django connects to the database and stores data in it**

### QuerySet
There is  a list of objects of the given model. QuerySet allows to read , filter and order data from the database.

### DjangoShell

In order to enable the Django shell run `python manage.py shell` in the local console.

Now try to   list all the posts 
 for that first `from blog.models import Post` then `Post.objects.all()`
 
**Creating Objects **

The post that already created are by the Django admin interface to create the python model run the command in the shell. `Post.object.create(author = me ,title = 'sample text' , text = 'test') `
Here the me is missing and it should be passed as a user model for that `from django.contrib.auth.models import User`

By default the username of the superuser will be taken , inorder to change the username `me =User.objects.get(username=<username >)`
