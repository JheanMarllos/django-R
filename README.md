Django R
========

Toolkit to use [Rethinkdb](https://rethinkdb.com) in Django. Features:

- Interface to explore the Rethinkdb data
- Helpers for basic operations

This module was made to give an easy access to the Rethinkdb functionalities inside of the Django environment. 
We are not trying to replace the classic Django orm nor the builtin Rethinkdb admin interface. It is just a set
of tools to ease the use of Rethinkdb in Django.

Install
-------

  ```python
pip install rethinkdb geojson jsonschema djangoajax six python-dateutil
pip install git+https://github.com/dmpayton/reqon.git
pip install git+https://github.com/JheanMarllos/django-R.git
  ```

Installed apps:

  ```python
'django_ajax',
'djR',
  ```

Urls: `url('^r/', include('djR.urls')),`

Optional settings
-----------------

  ```python
# default: 'localhost'
RETHINKDB_HOST = ip_here
# default: 28015
RETHINKDB_PORT = 28500
# default: None
R_DEFAULT_DB = "mydb"
# default: True
R_VERBOSE = False
  ```

Usage
-----

Go to `/r/` as superuser and start to explore the data.

Run a query:

  ```python
from rethinkdb import r
from djR.r_producers import R

q = r.db('mydb').table('mytable').limit(10)
results = R.run_query(q)
  ```

Run a query from json:

  ```python
from djR.r_producers import R

q = {"$db":"mydb", "$table":"mytable", "$query":[["$limit":10]]}
results = R.run_json(q)
  ```
  
Check the [Reqon doc](https://reqon.readthedocs.org/) for the json query format specifications.

Screenshot
----------

![Data explorer screenshot](https://raw.github.com/synw/django-R/master/docs/img/djR_explorer.png)

Todo
----

- Merge [django-changefeed](https://github.com/synw/django-changefeed) into here
- Add more query options: index, order, pluck, filters, etc..

Thanks
------

- To [Rethinkdb](https://rethinkdb.com)
- To [Reqon](https://github.com/dmpayton/reqon.git)
