# Flask-with-postgres
This example aims to demonstrate a simple way to connect a FLASK project to PostgresSQL database.  
(I repeat: only simple example !!!)

## PostgreSQL

Before run, i'm considering that POSTGRES is already properly installed and configured in your machine; just perform the following instructions:  
(don't forget to put the "values" in your "environment variable - DATABASE_URL")

create database ```<database_name>```;  
create user ```<user_name>``` with password '```<password>```';

alter role ```<user_name>``` set client_encoding to 'utf8';  
alter role ```<user_name>``` set default_transaction_isolation to 'read committed';  
alter role ```<user_name>``` set timezone to 'UTC';

grant all privileges on database ```<database_name>``` to ```<user_name>```;

alter database ```<database_name>``` owner to ```<user_name>```;

## Installing

To install and execution in your local machine, you will need to:

```
git clone https://github.com/RicardoTurco/flask-with-postgres.git && flask-with-postgres

Create and activate one "virtualenv"
(using any valid form) 

pip install -r requirements.txt

export APP_SETTINGS="config.DevelopmentConfig"
(or config.ProductionConfig, for this example, it doesn't matter.)

export DATABASE_URL="postgres://<user_name>:<password>@localhost:5432/<database_name>"

python manage.py db init
(Create MIGRATIONS directory structure;
This instruction is usually executed only once;)

python manage.py db migrate
(create migration file)

python manage.py db upgrade
(apply in database)

IMPORTANT: Every time there's a change in MODELs, just execute the last two instructions.

In the end, just check if the MODEL was applied in your database.
```

## Project Structure

```
├── flask-with-postgres
│   ├──  .gitignore
│   ├──  app.py
│   ├──  config.py
│   ├──  manage.py
│   ├──  models.py
│   ├──  README.md
│   ├──  requirements.txt
```

### Files

* `.gitignore` - Lists files and directories which should not be added to git repository.
* `app.py` - The Application entrypoint.
* `config.py` - Config file for envs, global config vars and so on.
* `manage.py` - The SQLAlchemy/Alembic entrypoint.
* `models.py` - Models of this example.
* `README.md` - Instructions and informations of this "challenge".
* `requirements.txt` - All project dependencies.


Based on article: "Flask by Example" (parts One and Two)  
```https://realpython.com/flask-by-example-part-1-project-setup/```

