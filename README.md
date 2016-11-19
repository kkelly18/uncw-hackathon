# UNCW Hackathon - TEAM GMO

Improve the process of maintaining oyster hatcheries and increase the amount of data available to researchers.

## Installation
This project is based off the pydanny's cookiecutter-django template.
See here for more information: https://github.com/pydanny/cookiecutter-django

Setup instructions compiled using Windows 10.  All tools are cross platform, but may follow an altered process.

1.) Install Python 2.7.X

https://www.python.org/downloads/release/python-2711/

2.) Install Git / GitHub GUI and Create an Account

https://desktop.github.com/

3.) Install postgres

https://www.postgresql.org/download/

4.) Install pgAdmin (Graphical Frontend for Postgres, Recommended!)

https://www.pgadmin.org/download/

5.) Install Node / NPM
https://nodejs.org/en/download/

6.) Create the database using pgAdmin.  If you did not do this step, use a command line tool.
```
Open the pgAdmin application.
Connect to the server using the credentials from installation.
Create a database name gmo.  The name must be gmo !
Save and leave the application open for later debugging.
```

7.) Clone this repo.  You can do this via the GUI or at the command line.  Then change into the directory.
```
git clone https://github.com/QuantScape/uncw-hackathon.git
cd uncw-hackathon/
```

8.) Make sure pip is on your path or use an absolute. Execute the following to build a virtual enviroment.
```python
pip install virtualenv
virtualenv .env/
.env/Scripts/activate
```

9.) Now install the required python dependencies (May take a few min).
```python
pip install -r ./gmo/requirements/local.txt
pip install -r ./gmo/requirements/base.txt
```

10.) Install Javascript Dependencies (May take a few min).
```
cd gmo
npm install
```
11.) Make local enviroment variable copy and use a text editor to fill out requisite variables (Mainly postgres settings).
```
mv env.example config/settings/.env
vim config/settings/.env
```

12.) Time to make initial database migrations.  These convert Django models to a SQL representation.
```python
python manage.py makemigrations
```

13.) If the above command executed without error, you can now commit the sql to the db.
```python
python manage.py migrate
```

##### Your enviroment and database is ready to rock.  

## Usage

#####  Serve application locally.
Install gulp globally (if you don't have it).  Change into the project directory and build the project with gulp.  This will run through a set of build tasks, and will serve the application on port 3000 on your local system (proxied for 8000).   Gulp will also watch for changes in the project files and update its content for live-reloading.  
``` 
npm install -g gulp  
cd uncw-hackathon/gmo
gulp watch
```


Check out this link for the needed browser extension for live-reloading:
http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-


##### Trouble with gulp?
```python
python manage.py runserver  # Serve app on port 8000, no minimization, or build tasks
```

##### Convert model creation/changes to SQL and commit to server
```python
python manage.py makemigrations
python manage.py migrate
```

##### Create an app
To create a new app, you must use the taskrunner (manage.py) and then move it into the project directory.  Then add the name for the app found in your-app-name/apps.py to the INSTALL_APPS in config/settings/common.py
```python
python manage.py startapp your-app-name
mv your-app-name gmo/
```


## Help

1.) python or pip not being recognized within the virtual enviroment.  
```
Check that you have activated your enviroment, .env/Scripts/activate
Check that these files exist within the .env/Scripts/
Execute the command using absolute paths.
```



## History

Project start date: 11/18/2016

## Credits

University of North Carolina at Wilmington.  
The entire staff of the CIE. 
All of our mentors and project partners.


## License

All content within is the sole property of the University of North Carolina at Wilmington.
All rights reserved.

