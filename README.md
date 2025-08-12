# AWAE preparation and notes
- [AWAE Course](https://portal.offsec.com/courses/web-300/books-and-videos/modules)
- [OSWE Exam Guide](https://help.offensive-security.com/hc/en-us/articles/360046869951-OSWE-Exam-Guide)

## Additional Resources (beyond the course)

| Name | URL |
| ------ | ------ |
| Z-r0crypt blog on OSWE preparation | [Blog](https://z-r0crypt.github.io/blog/2020/01/22/oswe/awae-preparation/) |
| jorgectf - OSWE Resources | [Gitbook](https://jorgectf.gitbook.io/awae-oswe-preparation-resources/) |
| Exploit writing for OSWE by rizemon| [Exploit writing](https://github.com/rizemon/exploit-writing-for-oswe) |
| NetSecFocus prep list| [oswe like VMs](https://docs.google.com/spreadsheets/d/1dwSMIAPIam0PuRBkCiDI88pU3yzrqqHkDtBngUHNCw8/edit?gid=665299979#gid=665299979) |

## Python notes

```python
# For sending HTTP requests
import requests

# For Base64 encoding/decoding
from base64 import b64encode, b64decode, urlsafe_b64encode, urlsafe_b64decode

# For getting current time or for calculating time delays
from time import time

# For regular expressions
import re

# For parsing HTTP cookies
from http import cookies

# For getting command-line arguments
import sys
```

### `requests` library
 - Methods
 ```python
 r = requests.get(url)
 r = requests.post(url, data={'key':'value'})
 r = requests.put(url, data={'key':'value'})
 r = requests.delete(url)
 r = requests.head(url)
 r = requests.options(url)
 
 # Reading HTTP response
  res = requests.get("https://github.com")

 # HTTP status code
res.status_code

# Body as a string
res.text

# Get response header
res.headers

```
- Passing params in URLs via GET
```python
 payload = {'key1': 'value1', 'key2': 'value2'}
 r = requests.get('https://github.com/get', params=payload)
 ```
- Sending cookie
```python
cookies = {
    "PHPSESSID": "testtest"
}

requests.get("https://github.com", cookies=cookies)
```
- Sending request through proxy
```python
proxies = {
    "HTTP": "http://127.0.0.1:8080",
    "HTTPS": "http://127.0.0.1:8080"
}

requests.get("https://github.com", proxies=proxies)
```
## Regex Notes 

| Pattern | Meaning | Example Match |
|---------|---------|---------------|
| `.` | Any character except newline | a.c → abc, axc |
| `^abc` | String starts with abc | abc123 |
| `abc$` | String ends with abc | 123abc |
| `a|b` | a or b | cat or bat |
| `ab*` | a followed by 0 or more b | a, ab, abb |
| `ab+` | a followed by 1 or more b | ab, abb |
| `ab?` | a followed by 0 or 1 b | a, ab |
| `[A-Za-z0-9]` | Any alphanumeric | A, 7 |
| `[^0-9]` | Not a digit | a, # |
| `\d` | Digit (0–9) | 5 |
| `\D` | Non-digit | x |
| `\w` | Word char [A-Za-z0-9_] | _ |
| `\W` | Non-word char | @ |
| `\s` | Whitespace | space, tab |
| `\S` | Non-whitespace | a |
