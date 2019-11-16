Flask restful api with blue_print on ubuntu 

How to run the App!

Install Docker version 18.06.1-ce, build e68fc7a
Install docker-compose version 1.22.0, build f46880fe
Install docker-machine version 0.14.0, build 89b8332

\$ cd to the project directory/

Build the modules and subsections using docker-compose

\$ docker-compose -f docker-compose-dev.yml up -d --build

Recreate the needed databases

\$ docker-compose -f docker-compose-dev.yml run lostfound-app python manage.py recreate-db

Populate the database with dummy (seed) data

\$ docker-compose -f docker-compose-dev.yml run lostfound-app python manage.py seed-db

Run the project

\$ docker-compose -f docker-compose-dev.yml up

to test email verification, uncomment 
            # token = generate_confirmation_token(new_user.email)
            # confirm_url = url_for('auth.confirm_email', token=token, _external=True)
            # content = confirm_url
            # subject = "Please confirm your email"
            # send_email(new_user.email, subject, content)
in the 'projectapiauth.py' in registration method.
define the smtp server parameter in the config file 
and also the mail authentication paramters in the docker-compose file.