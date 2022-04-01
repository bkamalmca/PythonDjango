# Profiles Rest API

Django Profiles Rest API project 

# Steps to install the django and setup projects
* Create the virtual environment  
  * `Run python3 -m venv <name_of_virtualenv>`
* Run the below to activate venv
  * `(base) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> ..\venv\Scripts\activate`
  * `(base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> pip install django`

* Run the below to create apps
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> django-admin startproject profiles_project .
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> python .\manage.py startapp profiles_api

# Setup project apps
1. Add the below in settings.py  
`rest_framework`    
 `rest_framework.authtoken`    
 `profiles_api`
2. Run the server  
   `python manage.py runserver 8080`
3. Update the code as given in models.py
4. Update the settings.py  
   `AUTH_USER_MODEL = 'profiles_api.UserProfile'`
5. Create migrations  
    `python manage.py makemigrations profiles_api`  
    `python manage.py migrate`

# Setup django admin
1. Create superuser
   `python manage.py createsuperuser`
2. Enable django admin - add to admin.py  
3. Test django admin

# Create API Views
* ### Describe logic, uses standard http methods, process files, calling other APIS
1. Update the file views.py in project profiles_api
   1. Get method api to display message
2. Create a new file - urls.py in project profiles_api
3. Update the urls.py in profiles_project to include the new app url
4. Test the new url in browser
   1. http://127.0.0.1:8080/api/hello-view/

# Create a serializer and methods
* ### To convert content into python object and vice versa
1. Create a new file serializers.py with content
2. Create a serializer class and create post method in views.py
3. Create put, post and delete methods
4. Test the API view

# Create a Viewsets (views.py)
* ### Use for Simple CRUD DB, Datastructures
1. Import viewset from rest_framework 
2. Create a class HelloViewSet and list function
3. Add URL router hellow-viewset in urls.py
4. Test the viewset in root url
   1. http://127.0.0.1:8080/api/
5. Add create, retrieve,.. functions
6. Test the viewset in root url
   1. http://127.0.0.1:8080/api/hello-viewset
   2. http://127.0.0.1:8080/api/hello-viewset/1

# Create Profile APIs
* Handle registration of new users nd validate profile data
* Listing existing profiles
