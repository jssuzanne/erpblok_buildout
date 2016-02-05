=======================
ERPBlok Buildout Recipe
=======================

This is a buildout recipe for `ERPBlok`_

The main goal of this recipe is to help you in : 

* Bootstrapping a new `ERPBlok`_ directories layout to start a new project
* Install all required dependencies in an isolated environment that does not mess up your main
  python path

.. _erpblok: https://bitbucket.org/jssuzanne/erpblok

System dependencies
-------------------

ERPBlok needs at least python 3.

You'll also need the python3-dev package in order to compile some dependencies
For example on debian based system (replace X by appropriate version)

    sudo apt-get install python3.X-dev 

ERPBlok use Postgresql and through SqlAlchemy

    sudo apt-get install postgresql

Installation
------------

Once you're done with system dependencies it's as easy as this :

Make a new virtualenv 

    pyvenv-3.3 erpblok_demo

Go into the new virtualenv and activate it

    cd erpblok_demo
    source ./bin/activate

Create a directory to store your project and change into it

    mkdir projects
    cd projects

Clone the current repository and give it your project name

    hg clone ssh://hg@bitbucket.org/jssuzanne/erpblok_buildout demo

Change to the project directory, bootstrap and build it

    cd demo
    ../bin/python3.3 bootstrap.py

Launch the buildout. Beware of launching it from the new bin directory created by the previous
command

    ./bin/buildout

Your environment is ready, You're done!

What has happened here ?
========================
The ./bin/buildout command as automatically get and install all the required dependencies using
the buildout.cfg file.
Look at buildout.cfg file to understand deeply the ERPBlok ecosystem.

How to run the whole stuff ?
============================

The buildout comes with a small ERPBlok example. You can delete it to create your own.
By the way if you want to try the demo, here are the steps to follow.

* Edit the erpblok.cfg file according to your database settings
* Create a new database

    ./bin/anyblok_pyramid -c erpblok.cfg

.. warning::

    anyblok_pyramid is only for test, if you want better wsgi server, install
    the gunicorn package and use this command::

        ./bin/gunicorn_anyblok_pyramid --anyblok-configfile erpblok.cfg -b 127.0.0.1:8080

Look at the `doc` directory of the main ERPBlok respository for more details.

https://bitbucket.org/jssuzanne/erpblok/

Contributing (hackers needed!)
==============================

ERPBlok is at a very early stage, so as this recipe.
Feel free to fork, talk with core dev, and spread the world!

Author
======
Jean-Sébastien Suzanne

License
=======
This is free software. License details comin soon.
