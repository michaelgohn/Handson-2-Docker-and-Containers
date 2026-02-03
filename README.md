1. I began this assignment by installing Docker on my computer and starting the Docker Desktop app.

2. I then pulled the PostgreSQL image:
   ```
   docker pull postgres
   ```
   I also started the postgres instance and interacted with it

4. I then defined my dependencies in requirements.txt

5. Then I copied the code from the instructions into my app.py file
```
import time
import redis from flask
import Flask app = Flask(__name__)
cache = redis.Redis(host='redis', port=6379)
def get_hit_count():
retries = 5
while True:
try:
return cache.incr('hits')
except redis.exceptions.ConnectionError as exc:
if retries == 0:
raise exc
retries -= 1
time.sleep(0.5)
@app.route('/')
def hello():
count = get_hit_count()
return 'Hello World! I have been seen {}
times.\n'.format(count)
```

5. After this I fixed the errors in the code. I did not realize that I needed to document these initially so from memory, I documented as many as I could in the Issues tab of this repo.

6. I then created a Dockerfile to containerize the application

7. I defined the services in compose.yaml and fixed some formatting errors

8. I built and ran the application and followed the provided link to the running app's browser interface

![Screenshot of Docker Desktop.](Screenshot%202026-02-03%20170822.png)

![Screenshot of Output page.](Screenshot%202026-02-03%20171124.png)
