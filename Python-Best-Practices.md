# Python Best Practices for Secure Coding

## 1. Use Latest Versions
Always use the latest versions of Python and its libraries.

## 2. Input Validation
a. Always validate and sanitize (or escape) all inputs

Example of escaping input using Node.js `escape-html`:

```python
escaped_input = html.escape(user_input)
```

b. Use parameterized queries to avoid SQLi attacks

Example without parameterized queries:

```python
# Python (using raw SQL - vulnerable!)
username = input("Enter username: ")
password = input("Enter password: ")

query = f"SELECT * FROM users WHERE username = '{username}' AND password = '{password}'"
cursor.execute(query)
```
Here, the attacker can enter `username = admin' --` and `password = anything` resulting in the query, `SELECT * FROM users WHERE username = 'admin' --' AND password = 'anything'
`

Example with parameterized queries:

```python
import sqlite3

conn = sqlite3.connect('users.db')
cursor = conn.cursor()

username = input("Enter username: ")
password = input("Enter password: ")

cursor.execute("SELECT * FROM users WHERE username = ? AND password = ?", (username, password))
```

## 3. Avoid Executing Dynamically Generated Code
Do not use functions such as `eval()`, `exec()` or `compile()` with dynamic inputs as attacker can use them to pass malicious code. Secure alternatives are:
* `ast.literal_eval()` which only evaluates simple data types:

```python
import ast

user_input = '{"name": "Alice", "age": 25}'
safe_obj = ast.literal_eval(user_input)
print(safe_obj)  # {'name': 'Alice', 'age': 25}
```

* Libraries like `sympy`, `simpleeval`, or `numexpr` to evaluate math expressions safely:

```python
from simpleeval import simple_eval

result = simple_eval("10 + 20 * (5 / 2)")
print(result)  # 60.0
```
* `RestrictedPython` (for sandboxed execution with limited functionality, e.g., in educational tools):

```python
from RestrictedPython import compile_restricted_exec
```

## 4. Dependency Management
a. Use tools `pipenv check` or `safety` to check for known vulnerabilities in your dependencies.
b. Minimize dependency use. Fewer dependies = smaller attack surfaces.

## 5. Proper Handling of Secrets
Do not hardcode secrets like DB passwords, secret keys directly in your code. Use secret management tools or environment variables instead.

```python
import os

API_KEY = os.environ.get("API_KEY")
```

## 6. Use Secure Transmission
Always use secure methods such as HTTPS when transmitting data over the internet.

```python
import requests

response = requests.get("https://www.example.com")
```

## 7. Implement Proper Logging
a. Logging is essential for debugging but you must make sure not to log sensitive information.
b. Review logs to ensure they don't expose secrets.

```python
import logging

logging.basicConfig(level=logging.INFO)

username = "user"
password = "password123"

logging.info(f"Username entered: {username}")
```

## 8. Use Encryption
Ensure to encrypt sensitive data when in storage and transit. You can use libraries like `cryptography` to implement symmetric and asymmetric encryptions.

```python
from cryptography.fernet import Fernet

key = Fernet.generate_key()
cipher_suite = Fernet(key)

cipher = cipher_suite.encrypt(b"Sensitive Data")
plaintext = cipher_suite.decrypt(cipher)
```

## 9. Limit Permissions
a. Apply least privilege with your Python apps.
b. Avoid running scripts as root or admin unless necessary.

## 10. Stay Current
Continuously educate yourself on new threats and vulnerabilities in the Python communities and security forums to stay up-to-date.

## References
1. Anna Isles. (August 26, 2023). Python Security Cheat Sheet for Developers. Aptori. https://www.aptori.com/blog/python-security-cheat-sheet-for-developers
