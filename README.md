# Python-Live-Project

## Introduction
Over the last two weeks of school work at The Tech Academy, I have been working on a Recipe Collection Program utilizing HTML, Python, Django, Css, and Bootstrap.

## HTML
The structure of the web page is built using HTML:
  
  <!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">

        <!--Links to Bootstrap-->
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.1.3/dist/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
        <!-- Link to Css styling  -->
        <link rel="stylesheet" href="{% static '/CSS/GrandmaCss.css' %}">

        <title>{% block title %}Grandmas Recipes{% endblock %}</title>
        <div class="nav">
                {% include "GrandmasRecipes/GrandmasRecipes_navbar.html" %}
        </div>
        <h1>"Keep Track of all your Grandmother's favorite Recipes"</h1>
    </head>
    <header>
        <div class="content">
            <p class="header">{% block header %}{% endblock %}</p><!--Space for individual page headers -->

        </div>
    </header>
    <body>
        <div>
            {% block content %}{% endblock %}
        </div>
    </body>
</html>

## Django
I then was able to leverage Static URL links to extend the above template as many times as necessary to build the web sites framework. 
Below are some snips of the extension of the base HTML through the static url links.
{% extends "GrandmasRecipes/GrandmasRecipes_base.html" %}
{% load static %}

{% block title %}Grandmas Recipe Collection{% endblock %}

{% block header %}<h4>Add to the Collection!</h4>{% endblock %}

{% block content %}
  <!-- Creates the form for user input-->
  <div id="form-container" >
    <form method="POST">
      {% csrf_token %}
      {{ form.as_p }}
      <button type="submit">Create Memory</button>
    </form>
  </div>
{% endblock %}


## Python
Using Python and Django together, I was able to make the website collect and retrieve user data from a database through the use of views functions. I was also able to
create a user input form through the Django Framwork.
Below is a view function that creates a recipe based on user inputs from the input form, and saves it to the database. 

def grandmas_create(request):
    form = RecipesForm(data=request.POST or None)
    if request.method == 'POST':
        if form.is_valid():
            form.save()
            return redirect('GrandmasRecipes_home')
    content = {'form': form}
    return render(request, 'GrandmasRecipes/GrandmasRecipes_create.html', content)
    

## CSS and Bootstrap
Using Css and Bootstrap I was able to style the objects to where and how I wanted the page to look. 

![image](https://user-images.githubusercontent.com/96742376/159068019-133ac894-181f-4bad-b51f-b8f5e37abd3c.png)


## Additional Skills Aquired
*As this was the first time we were asked to create something with little direction, I had to rely on researching a lot of the goals that I wanted for my page.
*Working with SqLite3 DB
*Agile and Scrum
*Version ControL and Branch Management
*Virtual Environments
