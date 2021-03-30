# Django 2.2 project template

##### Requrements:
 - Python 3.5
 - Django 2.2.* (+ psycopg2)
 - PostgreSQL >= 9
 - Node.js >= 10.10

##### Packages
* [Catalog](https://github.com/redsolution/django-catalog-tree)
* [Menu](https://github.com/redsolution/django-treemenus)
* [Import-redirects](https://github.com/redsolution/django-import-redirects)
* [Seo](https://github.com/redsolution/django-seo)
* [News](https://github.com/redsolution/django-easy-news)
* [Chunks](https://github.com/redsolution/django-chunks)
* [Attachments](https://github.com/redsolution/django-tinymce-attachment)
* [Feedback](https://github.com/redsolution/django-simple-feedback)
* [Google ReCaptcha v2](https://github.com/redsolution/django-nocaptcha-recaptcha)
* [CMS](https://github.com/redsolution/django-page-cms)
* [Filebrowser](https://github.com/redsolution/django-filebrowser-no-grappelli)

##### Installation
Create bash file "new_project.sh" in your projects directory with following content:
``` sh
#!/bin/bash
project_name=$1
git_url=
#
python3 -m venv $project_name/venv
. $project_name/venv/bin/activate
#pip install Django==2.2.*
#pip install python-memcached
#pip install psycopg2-binary==2.8.5
cd $project_name/
django-admin startproject -e py,js,json,gitignore --template=https://github.com/shoker174/django-box-1/archive/master.zip $project_name .
pip install -r requirements.txt
createdb $project_name
python init_settings.py
rm init_settings.py
rm readme.md
python manage.py migrate
python manage.py loaddata $project_name/fixtures/db.json
python manage.py init_catalog
npm i
git init
git remote add origin $git_url/$project_name
python manage.py runserver 0:8000
```
Run bash script with project_name parameter, like this:
``` sh
. new_project.sh project_name
```
After installation project will be available at [localhost:8000](http://localhost:8000)
