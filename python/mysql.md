## install  mysql-python

```

sudo -H pip install mysql-python

Traceback (most recent call last):
  File "setup.py", line 15, in <module>
    metadata, options = get_config()
  File "/usr/lib/python2.5/MySQL-python-1.2.3/setup_posix.py", line 43, in get_config
    libs = mysql_config("libs_r")
  File "/usr/lib/python2.5/MySQL-python-1.2.3/setup_posix.py", line 24, in mysql_config
    raise EnvironmentError("%s not found" % (mysql_config.path,))
EnvironmentError: mysql_config not found

```

sudo apt-get install libmysqlclient-dev



## install PyMySQL

pip install PyMySQL
