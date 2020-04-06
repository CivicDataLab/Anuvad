## Fork of Weblate

### Installation

Install on Debian and Ubuntu:

*System requirements*

```
apt install \
   libxml2-dev libxslt-dev libfreetype6-dev libjpeg-dev libz-dev libyaml-dev \
   libcairo-dev gir1.2-pango-1.0 libgirepository1.0-dev libacl1-dev libssl-dev \
   build-essential python3-gdbm python3-dev python3-pip python3-virtualenv virtualenv git
```

*Databases used*

1. Postgresql
2. Redis

*Python Modules*

```
pip install -e weblate
```

1. Copy the file weblate/weblate/settings_example.py to weblate/weblate/settings.py
2. Adjust the values in the new `settings.py` file to your liking.
3. Create the database and migrate using `weblate migrate`
4. Create the administrator user account and copy the password it outputs to the clipboard, and also save it for later use: `weblate createadmin`
5. Collect static files for webserver using `weblate collectstatic`
6. Start celery workers using `weblate/weblate/examples/celery start`
7. Start dev server: `weblate runserver`
