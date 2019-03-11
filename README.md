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




```

```sh
locust --host=http://example.com
locust -f locust_files/my_locust_file.py --host=http://example.com
locust -f locust_files/my_locust_file.py --master --host=http://example.com
locust -f locust_files/my_locust_file.py --slave --host=http://example.com
locust -f locust_files/my_locust_file.py --slave --master-host=192.168.0.100 --host=htp://example.com
```

```
```


