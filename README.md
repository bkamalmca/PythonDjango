# Profiles Rest API

## Django Profiles Rest API project   
The sample project to create user profile, authentication modules and profile feeds using django framework.   
It includes from install django, setup and code.
Prerequisite is little knowledge about rest api and python.

## Steps to install the django and setup projects
* Create the virtual environment  
  * `Run python3 -m venv <name_of_virtualenv>`
* Run the below to activate venv
  * `(base) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> ..\venv\Scripts\activate`
  * `(base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> pip install django`

* Run the below to create apps
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> django-admin startproject profiles_project .
  * (base) (venv) PS C:\Users\kamalakannan.x.balak\PythonDjango\profiles-rest-api> python .\manage.py startapp profiles_api

## Setup project apps
1. Add the below in settings.py  
 `rest_framework`    
 `rest_framework.authtoken`    
 `profiles_api`
2. Run the server  
   `python manage.py runserver 8080`
3. Update the code as given in models.py
4. Update the settings.py  
   `AUTH_USER_MODEL = 'profiles_api.UserProfile'`
5. Create migrations to create db tables 
    `python manage.py makemigrations profiles_api`  
    `python manage.py migrate`

## Setup django admin
1. Create superuser
   `python manage.py createsuperuser`
2. Enable django admin - add to admin.py  
3. Test django admin

## Create API Views
* ### Describe logic, uses standard http methods, process files, calling other APIS
1. Update the file views.py in project profiles_api
   1. Get method api to display message
2. Create a new file - urls.py in project profiles_api
3. Update the urls.py in profiles_project to include the new app url
4. Test the new url in browser
   1. http://127.0.0.1:8080/api/hello-view/

## Create a serializer and methods
* ### To convert content into python object and vice versa
1. Create a new file serializers.py with content
2. Create a serializer class and create post method in views.py
3. Create put, post and delete methods
4. Test the API view

## Create a Viewsets (views.py)
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

## Create Profile APIs
* Handle registration of new users and validate profile data
* Listing existing profiles
* View specific profiles
* Update profile of user
* Delete user
* URL - /api/profile - List (GET), New (POST)
* /api/profile/<profile_id> - GET, update (PUT/PATCH), DELETE
1. Create a new user profile serializer class in serializer.py
   1. from profiles_api import models 
   2. class meta, functions - create, update(password hashing)
2. Create a user profile viewset in views.py
   1. from profiles_api import models
   2. use ModelViewSet to connect serializer and provide query set to ModelViewSet
3. Register profile viewset in urls.py
4. Test creating a profile
   1. http://127.0.0.1:8080/api/profile
   2. http://127.0.0.1:8080/api/profile/1
5. Create permission class (permissions.py)
   1. Only the user can change their own profile
   2. create class UpdateOwnProfile
6. Add authentication and permissions to viewset
   1. Import authentication in views.py and permissions
   2. Add auth class in UserProfileViewSet
   3. Add permission class 
7. Test new permissions
   1. Modify option (PUT/PATCH) is not available now
8. Add search profiles feature
   1. Import filters in views.py
   2. Add filters to UserProfileViewSet
   3. Add search fields
9. Test searching profiles
   1. Filters option in http://127.0.0.1:8080/api/profile/
   2. http://127.0.0.1:8080/api/profile/?search=Kam

## Create login API
1. Create login API Viewset in views.py
   1. import ObtainAuthToken, api_settings
   2. Create new class UserLoginApiView
   3. Update urls.py to include login endpoint
2. Test login API
   1. http://127.0.0.1:8080/api/login
   2. Django builtin login & use user account
   3. Get the token for auth
3. Set token header using Chrome ModHeader extension
   1. set in extension Authorization = Token <Tokenid>
   2. Modify the username and test it
   3. After testing, disable the Authorization
   
## Create profile feed API
* Create new feed items, update, delete
* /api/feed/ - list all, GET, POST (create new)
* /api/feed/<feed_id> - manage feed, GET, PUT/PATCH, DELETE
1. Import settings in models.py
2. Create a new class - ProfileFeedItem to store, manage in DB
3. Create and run model migration  
   `python manage.py makemigrations`
4. Look for auto-created file in migrations directory  
   `python manage.py migrate`
5. Register the ProfileFeedItem in admin.py
6. Create a profile feed class in serializers.py
7. Create a viewset for profile feed item in views.py
8. Add the feed router in urls.py
9. Test feed API
   1. Enable the authorization in extension
   2. http://127.0.0.1:8080/api/feed
   3. Edit feed - http://127.0.0.1:8080/api/feed/1
10. Add permissions to feed API 
    1. Create a new class UpdateOwnStatus in permissions.py
    2. Import permissions IsAuthenticatedOrReadOnly in views.py
    3. Add permission_classses in UserProfileFeedViewSet of views.py
11. Test feed API permissions
    1. Users can see other feed but cannot modify others
    2. Test with two users profile and authorization token
12. Restrict viewing satus updates to logged in users only
    1. Now, restrict to view only their feeds
    2. Update permission from IsAuthenticatedOrReadOnly to IsAuthenticated in views.py
13. Test new private feed
    1. Now, the endpoint is locked to authenticated users only
    2. Disable authorization and try. Feed is not accessible

## The course is complete. Happy learning...