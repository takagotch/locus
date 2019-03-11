### locus
---
https://github.com/locustio/locust

https://docs.locust.io/en/stable/index.html

```py
from locust import HttpLocust, TaskSet

def login(l):
  l.client.post("/login", {"username":"elen_key", "password":"education"})
  
def logout(l):
  l.client.post("/logout", {"username":"ellen_key", "password":"education"})
  
def index(l):
  l.client.get("/")

def profile(l):
  l.client.get("/profile")

class UserBehavior(TaskSet):
  tasks = {index: 2, profile: 1}
  
  def on_start(self):
    login(self)
    
  def on_stop(self):
    logout(self)

class WebsiteUser(HttpLocust):
  task_set = UserBehavior
  min_wait = 5000
  max_wait = 9000


from locust import HttpLocust, TaskSet, task

class UserBehavior(TaskSet):
  def on_start(self):
    """ on_start is called when a Locust start before any task is scheduled """
    self.login()
    
  def on_stop(self):
    """ on_stop is called when the TaskSet is stopping """
    self.logout()
    
  def login(self):
    self.client.post("/login", {"username":"ellen_key", "password":"education"})
    
  def logout(self):
    self.client.post("/logout", {"username":"ellen_key", "password":"education"})

  @task(2)
  def index(self):
    self.client.get("/")
    
  @task(1)
  def profile(self):
    self.client.get("/profile")
    
class WebSiteUser(HttpLocust):
  task_set = UserBehavior
  min_wait = 5000
  max_wait = 9000
  

import random

class WebsiteUser(HttpLocust):
  task_set = UserBehaviour
  wait_function = lambda self: random.expovariate(1)*1000


from locust import Locust, TaskSet, task

cass MyTaskSet(TaskSet):
  @task
  def my_task(self):
    print("executing my_task")
    
class MyLocust(Locust):
  task_set = MyTaskSet
  min_wait = 5000
  max_wait = 15000
  
class WebUserLocust(Locust):
  weight = 3

class MobileUserLocust(Locust):
  wight = 1


from locust import Locust, TaskSet, task

class MyTaskSet(TaskSet):
  @task
  def my_task(self):
    print("Locust instance (%r) executing my_task" % (self.locust))
    
class MyLocust(Locust):
  task_set = MyTaskSet


from locust import Locust, TaskSet, task

class MyTaskSet(TaskSet):
  min_wait = 5000
  max_wait = 15000
  
  @task(3)
  def task1(self):
    pass
    
  @task(6)
  def task2(self):
    pass
    
class MyLocust(Locust):
  task_set = MyTaskSet


from locust import Locut, TaskSet

def my_task(1):
  pass

class MyTaskSet(TaskSet):
  tasks = [my_task]

class MyLocust(Locust):
  task_set = MyTaskSet


class ForumPage(TaskSet):
  @task(20)
  def read_thread(self):
    pass
  
  @task(1)
  def new_thread(self):
    pass
    
  @task(5)
  def stop(self):
    self.interrupt()
    
class userBehaviour(TaskSet):
  tasks = {ForumPage:10}
  
  @task
  def index(self):
    pass

class MyTaskSet(TaskSet):
  @task
  class SubTaskSet(TaskSet):
    @task
    def my_task(self):
      pass

class MyTaskSequence(TaskSequence):
  @seq_task(1)
  def first_task(self):
    pass
    
  @seq_task(2)
  def second_task(self):
    pass
    
  @seq_task(3)
  @task(10)
  def thrid_task(self):
    pass


from locust import HttpLocust, TaskSet, task

class MyTaskSet(TaskSet):
  @task(2)
  def index(self):
    self.client.get("/")

  @task(1)
  def about(self):
    self.client.get("/about/")

class MyLocust(HttpLocust):
  task_set = MyTaskSet
  min_wait = 5000
  max_wait = 15000


response = self.client.get("/about")
print("Response status code:", response.status_code)
print("Response content:", response.text)

response = self.client.post("/login", {"username":"testuser", "password":"secret"})

with client.get("/", catch_response=True) as response:
  if response.content != b"Success":
    response.failure("Got wrong response")

with client.get("/does_not_exist/", catch_reponse=True) as response:
  if response.status_code == 404:
    reponse.success()
    
for i in range(10):
  client.get("/blog?=%i" % i, name="/blog?id=[id]")

sys.path.append(os.getcwd())
import common.auth
```

```sh
locust -f locust_file.py WebUserLocust MobileUserLocust

locust --host=http://example.com
locust -f locust_files/my_locust_file.py --host=http://example.com
locust -f locust_files/my_locust_file.py --master --host=http://example.com
locust -f locust_files/my_locust_file.py --slave --host=http://example.com
locust -f locust_files/my_locust_file.py --slave --master-host=192.168.0.100 --host=htp://example.com
```

```
```


