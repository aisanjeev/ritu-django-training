1. Import BootStrap and FontAwesome
``` shell

.2 Wrap forloop around new Bootstrap/Div elements in welcome.html

 3 Create 'top-menu.html' and include it in your base HTML

 4. Add a posts/forms.py

5. Create the function 'new' in post/views.py and import the form


5. Create a template named 'new.html'
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

4. Add URL pattern
``` shell
    path('new', new),
```

5. Add additional logic to posts/new
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

6. 
``` shell
#Add widget to make text field look bigger
        widgets = {
            'body': Textarea()
        }
```