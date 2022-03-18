# Profiles Rest API

Django Profiles Rest API project 

# Steps to install the django and setup projects
* Create the virtual environment
* Run the below to activate venv

  * (base) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> ..\venv\Scripts\activate
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> pip install django

* Run the below to create apps
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> django-admin startproject profiles_project .
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> python .\manage.py startapp profiles_api

# Setup project apps
1. Add the below in settings.py  
rest_framework  
rest_framework.authtoken  
profiles_api  

2. Run the server  
   python manage.py runserver 8080

3. Update the code as given in models.py
4. Update the settings.py  
   AUTH_USER_MODEL = 'profiles_api.UserProfile'
5. Create migrations  
   python manage.py makemigrations profiles_api  
   python manage.py migrate
6. 
