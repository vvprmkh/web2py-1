## Azure Web Apps version
https://groups.google.com/forum/#!searchin/web2py/azure/web2py/XGxM_Tb9nJ4/ItS8GF5oAgAJ

web2py setup Azure Web Apps.

Based on https://azure.microsoft.com/en-us/documentation/articles/web-sites-python-configure/

1. Create web app on Azure Portal
2. Fork a repo web2py (github)
3. Add 4 files  to own github repository (web2py/)
    - ptvs_virtualenv_proxy.py
    - requirements.txt
    - runtime.txt
    - web.config
4. Configure continuous deployment using github https://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/ 
look Deploy files from a repository site like BitBucket, CodePlex, Dropbox, GitHub, or Mercurial. 
Azure creates an association with the selected repository, and pulls in the files from the specified branch. After this process completes, the Deployment section of your web app's blade will show an Active Deployment message that indicates deployment has succeeded.
5. Run web app on on Azure Portal

Admin password:
1.on local copy web2py - save the password in the parameters_8000.py file
2.rename parameters_8000.py parameters_443.py
3.copy parameters_443.py via FTP (link in Azure Portal) in site/wwwroot

Example: 
https://nbush2py.azurewebsites.net
https://github.com/Nbushkov/web2py

## Readme

web2py is a free open source full-stack framework for rapid development of fast, scalable, secure and portable database-driven web-based applications. 

It is written and programmable in Python. LGPLv3 License

Learn more at http://web2py.com

## Google App Engine deployment

    cp examples/app.yaml ./
    cp handlers/gaehandler.py ./
    
Then edit ./app.yaml and replace "yourappname" with yourappname.

## Important reminder about this GIT repo

An important part of web2py is the Database Abstraction Layer (DAL). In early 2015 this was decoupled into a separate code-base (PyDAL). In terms of git, it is a sub-module of the main repository.

The use of a sub-module requires a one-time use of the --recursive flag for git clone if you are cloning web2py from scratch.

    git clone --recursive https://github.com/web2py/web2py.git

If you have an existing repository, the commands below need to be executed at least once:

    git submodule update --init --recursive

If you have a folder gluon/dal you must remove it:

    rm -r gluon/dal

PyDAL uses a separate stable release cycle to the rest of web2py. PyDAL releases will use a date-naming scheme similar to Ubuntu. Issues related to PyDAL should be reported to its separate repository.


## Documentation (readthedocs.org)

[![Docs Status](https://readthedocs.org/projects/web2py/badge/?version=latest&style=flat-square)](http://web2py.rtfd.org/)

## Tests

[![Build Status](https://img.shields.io/travis/web2py/web2py/master.svg?style=flat-square&label=Travis-CI)](https://travis-ci.org/web2py/web2py)
[![MS Build Status](https://img.shields.io/appveyor/ci/web2py/web2py/master.svg?style=flat-square&label=Appveyor-CI)](https://ci.appveyor.com/project/web2py/web2py)
[![Coverage Status](https://img.shields.io/codecov/c/github/web2py/web2py.svg?style=flat-square)](https://codecov.io/github/web2py/web2py)


## Installation Instructions

To start web2py there is NO NEED to install it. Just unzip and do:

    python web2py.py

That's it!!!

## web2py directory structure

    project/
        README
        LICENSE
        VERSION                    > this web2py version
        web2py.py                  > the startup script
        anyserver.py               > to run with third party servers
        ...                        > other handlers and example files
        gluon/                     > the core libraries
            packages/              > web2py submodules
              dal/
            contrib/               > third party libraries
            tests/                 > unittests
        applications/              > are the apps
            admin/                 > web based IDE
                ...
            examples/              > examples, docs, links
                ...
            welcome/               > the scaffolding app (they all copy it)
                ABOUT
                LICENSE
                models/
                views/
                controllers/
                sessions/
                errors/
                cache/
                static/
                uploads/
                modules/
                cron/
                tests/
            ...                    > your own apps
        examples/                  > example config files, mv .. and customize
        extras/                    > other files which are required for building web2py
        scripts/                   > utility and installation scripts
        handlers/
            wsgihandler.py         > handler to connect to WSGI
            ...                    > handlers for Fast-CGI, SCGI, Gevent, etc
        site-packages/             > additional optional modules
        logs/                      > log files will go in there
        deposit/                   > a place where web2py stores apps temporarily

## Issues?

Report issues at https://github.com/web2py/web2py/issues
