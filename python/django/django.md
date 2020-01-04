

# Django

## General
- kill running server `$ sudo lsof -t -i tcp:8000 | xargs kill -9`
- create environment `$ python3 -m venv ./env`
- start env `$ source env/bin/activate`
- Set env variable:
    - ` vim ~/.bash_profile` add key like `export SOME_KEY='<key here>'` 
    - import in settings.py `key = os.environ.get('SOME_KEY')`
    - run `source ~/.bash_profile`