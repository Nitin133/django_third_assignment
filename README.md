# django_third_assignment

Django Third Assignment
This Assignment is extension of Django Second Assignment

Consider you have to Develop a Software for Managing a Zoo. The zoo is divided into 3 categories Mammals, Birds, and Fish life. Zoo wants to manage the following features for each category:

Mammal

Name (name) -> String
Species (species) -> String
The food they eat (food) -> string
Last Feed Time (last_feed_time)-> Date Time
Gender (gender) -> 2 choices (M, F)
Bird

Name (name) -> String
Species (species) -> String
The food they eat (food)-> String
Last Feed Time (last_feed_time)-> Date Time
Fish

Color (color) -> String
Species (species) -> String
The Food they eat (food) -> String
Count (count) -> Integer
Last Feed Time (last_feed_time) > Date Time
Reason there is no name in the Fish is because Fish are majory in groups in a Zoo. Hence it has a count

Assignment:
Create a Django app named animals
Create 3 models in animals app -> Mammal, Bird and Fish with features mentioned above
Do not change Database changes in settings.py
Run makeMigrations command
Finally, run migrate command to create tables in the database
Create views to Get and POST Data for Mammals, Bird, Fish Models Hint: Use ORM
For Views and Urls More Details are given below
Some Guide for urls.py:
Name in Django URL -> name is used for accessing that URL from your Django / Python code.
For example you have this in animals/urls.py
url(r'^main/', views.main, name='main')
In point 2, "main" is the name of this URL
URL namespaces -> URL namespaces allow you to uniquely reverse named URL patterns even if different applications use the same URL names. At Line 21 in zoo/urls.py, path('', include((animals.urls', animals),namespace=animals) ), namespace=animals) is set. Remember, Both Name and Namespace are important for the assignment
For this assignment's test cases we have used some predefined names and namespace
Those names are defined below in the problem statement describes as "Django Url name"
Please make sure you use those names in Django URLs or else your assignment's test will fail Summary: Namespace is "animals" set in zoo/urls.py file and name is to be set for each URL in animals/urls which is stated in the problem statement
Views: Expected I/O
Part 1: GET, POST, PUT and DELETE request for fetching Mammals

Django URL name: mammals
No parameter

Actions:

GET - get list of all or one mammal
POST - Add a new mammal to the Zoo
PUT - Feed the Mammal i.e Update last_feed_time to current time
DELETE - Remove Animal from the zoo

  1. GET:
     Part 1:
        
        Response Data format {"data": [name,species,gender,food]}
        If no data is present
        /animals/mammals/
        Response -> {‘data’: []}


        /animals/mammals
         Response ->{"data": [["lion", "Panthera", "M", "meat"], ["tiger", "Panthera", "M", "chicken"]]}
    
    Part 2:
         Response Data format {"name": name, "species": species, "gender": gender, "food": food}
        /animals/mammals/lion
         Response ->{"name": "lion", "species": "Panthera", "gender": "M", "food": "meat"}


  2. POST
  Response Data format {"created": {"name": name}}
  /animals/mammals/ -d "name=lion&species=Panthera&gender=M&food=meat"
  Response -> {"created": {"name": "lion"}}
  
  3. PUT
  Response Data format {"Feeded": name}
  /animals/mammals/lion
  Response -> {"Feeded": "lion"}
  
  4. DELETE 
  Response Data format {"Deleted ": name}
  /animals/mammals/lion
  Response -> {"Deleted": "lion"}
Part 2: GET, POST, PUT and Delete request for fetching Birds

Django URL name: birds
No parameter

Actions:

GET - get list of all or one Birds
POST - Add a new bird to the Zoo
PUT - Feed the Bird i.e Update last_feed_time to current time
DELETE - Remove Bird from the zoo

  1. GET:
  Part 1:
        Response Data format {"data": [name,species,food]}
        If no data is present
        /animals/birds/
        Response -> {"data": []}

        /animals/birds/
         Response ->{"data": [["Parrot", "parrata", "insects"]]}
      
   Part 2:
         Response Data format {"name": name, "species": species, "food": food}
        /animals/birds/Parrot
         Response ->{"name": "Parrot", "species": "parrata", "food": "insects"}
   


  2. POST
  Response Data format {"created": {"name": name}}
  /animals/birds/ -d "name=Parrot&species=parrata&food=insects"
  Response -> {"created": {"name": "Parrot"}}
  
  3. PUT
  Response Data format {"Feeded": name}
  /animals/birds/Parrot
  Response -> {"Feeded": "Parrot"}
  
  4. DELETE 
  Response Data format {"Deleted ": name}
  /animals/birds/Parrot
  Response -> {"Deleted": "Parrot"}
Part 3: GET, POST and DELETE request for fetching Fishes


Django URL name: fishes
No parameter

Actions

GET - get list of all or one Fish species

POST - Add a new fish species to the Zoo

PUT - Feed the Fish species i.e Update last_feed_time to current time

DELETE - Remove Fish species from the zoo

     1. GET:
       Part 1:
           Response Data format {"data": [name,species,food]}

           If no data is present
           /animals/fishes/
           Response -> {"data": []}

           /animals/fishes/
           Response ->{"data": ["yellow", "GoldFisha", "grain", 100]}

      Part 2:
            Response Data format {"color": color, "species": species, "food": food,"count" : count }
           /animals/fishes/GoldFisha
            Response ->{"color": "yellow", "species": "GoldFisha", "food": "grain", "count": 100}


     2. POST
     Response Data format {"created": {"species": species}}
     /animals/fishes/ -d "color=yellow&species=GoldFisha&food=grain&count=2000"
     Response -> {"created": {"species": "GoldFisha"}}

     3. PUT
     Response Data format {"Feeded": species}
     /animals/fishes/GoldFisha
     Response -> {"Feeded": "GoldFisha"}

     3. DELETE 
     Response Data format {"Deleted ": species}
     /animals/fishes/GoldFisha
     Response -> {"Deleted": "GoldFisha"}
Installation Steps
Open up your Terminal / Command Line
git clone the repository
cd into the directory of the step (the one you just git cloned)
make sure you have python3 installed
Install virtualenv by following the steps
Mac
python3 -m pip install --user virtualenv
python3 -m venv env
source env/bin/activate

Windows
py -m pip install --user virtualenv
py -m venv env
.\env\Scripts\activate
Run
python -m pip install -r requirements/requirements.txt
No Database setup needs to be done. Do not edit Database settings in settings.py

If everything runs fine till here, create the application using the command

python manage.py startapp animals
Now uncomment the following lines
Line 21 in zoo/urls.py -> path('animals/', include(('animals.urls', 'animals'), namespace='animals')),
Line 40 in zoo/settings.py -> 'animals',
Now Create File animals/urls.py and add lines

from django.urls import path

from . import views
urlpatterns = []
Run
python manage.py makemigrations
Now Run the Server using command
python manage.py runserver
Great! Start Coding the assignment for above usecase
After Finishing the assignment, you can test them locally using command
coverage run --source='.' manage.py test --no-input
Push the code into the repo using git, Check Pull Requests Tab. Open PR #1
Check if all the tests are Passed
Contact TA for the review
