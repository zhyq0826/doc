### celery

异步任务队列库，支持redis，rabbitMQ，mongodb等众多数据库


#### install

```
pip install celery

```

#### 开始使用celery


1. 创建 tasks.py

```

from celery import Celery

app = Celery('tasks', broker='redis://localhost')

@app.task
def add(x, y):
    return x + y

```


2. 执行 worker

```
celery -A tasks worker --loglevel=info

```

3. 执行task 

在当前路径下执行 call task

```
#导入创建的tasks模块
from tasks import add 

result = add.delay(4,4)

```

delay 返回一个 AsyncResult 实例，在这个例子中, 返回的实例如果调用

```
result.ready()

```

抛出异常

```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "C:\Python27\lib\site-packages\celery\result.py", line 254, in ready
    return self.state in self.backend.READY_STATES
  File "C:\Python27\lib\site-packages\celery\result.py", line 390, in state
    return self._get_task_meta()['status']
  File "C:\Python27\lib\site-packages\celery\result.py", line 327, in _get_task_meta
    meta = self.backend.get_task_meta(self.id)
  File "C:\Python27\lib\site-packages\celery\backends\base.py", line 291, in get_task_meta
    meta = self._get_task_meta_for(task_id)
AttributeError: 'DisabledBackend' object has no attribute '_get_task_meta_for'


```


4. worker 加入backend

```
app = Celery('tasks', backend='redis://localhost', broker='redis://localhost')

```

5. 重新启动worker， 重新导入task 执行task


```

#任务执行状态
result.ready()  

#任务执行结果
result.get(timeout=1)  

#禁止异常抛出
result.get(propagate=False) 

#异常栈
result.traceback 

```


#### 在app 中使用celery


1. 创建project

```
proj/__init__.py
    /celery.py
    /tasks.py

```


**proj/celery.py**

```

from __future__ import absolute_import

from celery import Celery

app = Celery('proj',
             broker='amqp://',
             backend='amqp://',
             include=['proj.tasks'])

# Optional configuration, see the application user guide.
app.conf.update(
    CELERY_TASK_RESULT_EXPIRES=3600,
)

if __name__ == '__main__':
    app.start()

```

**proj/tasks.py**


```
from __future__ import absolute_import

from proj.celery import app


@app.task
def add(x, y):
    return x + y


@app.task
def mul(x, y):
    return x * y


@app.task
def xsum(numbers):
    return sum(numbers)

```

**执行worker**

在proj目录

```

$ celery -A proj worker -l info

[2014-09-17 13:17:32,287: WARNING/MainProcess] /usr/local/lib/python2.7/dist-packages/celery/apps/worker.py:161: CDeprecationWarning: 
Starting from version 3.2 Celery will refuse to accept pickle by default.

The pickle serializer is a security concern as it may give attackers
the ability to execute any command.  It's important to secure
your broker from unauthorized access when using pickle, so we think
that enabling pickle should require a deliberate action and not be
the default choice.

If you depend on pickle then you should set a setting to disable this
warning and to be sure that everything will continue working
when you upgrade to Celery 3.2::

    CELERY_ACCEPT_CONTENT = ['pickle', 'json', 'msgpack', 'yaml']

You must only enable the serializers that you will actually use.


  warnings.warn(CDeprecationWarning(W_PICKLE_DEPRECATED))
 
 -------------- celery@zhyq v3.1.15 (Cipater)
---- **** ----- 
--- * ***  * -- Linux-3.13.0-24-generic-i686-with-Ubuntu-14.04-trusty
-- * - **** --- 
- ** ---------- [config]
- ** ---------- .> app:         proj:0xb6c3bf4c
- ** ---------- .> transport:   redis://localhost:6379//
- ** ---------- .> results:     redis://localhost
- *** --- * --- .> concurrency: 4 (prefork)
-- ******* ---- 
--- ***** ----- [queues]
 -------------- .> celery           exchange=celery(direct) key=celery
                

[tasks]
  . proj.tasks.add
  . proj.tasks.mul
  . proj.tasks.xsum

[2014-09-17 13:17:32,298: INFO/MainProcess] Connected to redis://localhost:6379//
[2014-09-17 13:17:32,303: INFO/MainProcess] mingle: searching for neighbors
[2014-09-17 13:17:33,309: INFO/MainProcess] mingle: all alone
[2014-09-17 13:17:33,319: WARNING/MainProcess] celery@zhyq ready.


```




