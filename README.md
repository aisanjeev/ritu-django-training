# ritu-django-training
1. Setup ENV and Install Django
``` shell
#Make sure python is installed
python --version
python -m venv venv
.\venv\Scripts\activate
pip install django
python -m django --version
```


2. Create project
``` shell
django-admin startproject blog
cd blog
```

3. Run the server
``` shell
python manage.py runserver
python manage.py runserver 0:8000
```

4. Create a website folder to hold the views
``` shell
python manage.py startapp website
```

5. Under planner/settings.py: add website to the INSTALLED_APPS list 
``` shell
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'website',
]
```

6. Make a welcome view in website/views.py
``` shell
#Import the HttpResponse object
from django.http import HttpResponse

#The welcome view
def welcome(request):
    return render(request, "website/welcome.html")

7. Make a templates folder in the website app
``` shell
#Create the folder structure through IDE GUI or with the commands below
mkdir website/templates
touch website/templates/website/welcome.html
#Put whatever you want into html file
```


8. Modify urls.py to add the website views
``` shell
#Import the views
from website.views import welcome
# To to urlpatterns in blog/urls.py
path('', welcome, name='welcome')
 9.Import BootStrap and FontAwesome
``` shell
10. Wrap forloop around new Bootstrap/Div elements in welcome.html
11.Create 'top-menu.html' and include it in your base HTML
12.Add a posts/forms.py
13. Create the function 'new' in post/views.py and import the form
14.Create a template named 'new.html'
``` shell
{% extends "base.html" %}
{% block title %}Create Post {% endblock %}
{% block content %}
<h2>Create a Post</h2>
<form method="post">
    <table>
        {{ form }}
    </table>
    {% csrf_token %}
    <button type="submit">Create</button>
</form>
{% endblock %}
```
15. Add URL pattern
``` shell
    path('new', new),
```
16. Add additional logic to posts/new
``` shell
    if request.method == "POST":
        form = PostForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect("/")  
    else:
        form = PostForm()
    return render(request, "posts/new.html", {"form": form })
```

