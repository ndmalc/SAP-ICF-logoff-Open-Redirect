# SAP-ICF logoff Open Redirect
## Description

SAP ICF provides a `logoff` functionality that exposes a `redirecturl` `GET` parameter. When redirection is not restricted by configuration the `logoff` is vulnerable to an Open Redirect.

Vulnerability is probably applicable to a wide number of version. No public details known.

This repository provides a POC for an Open Redirection on a SAP ICF component.

## How to exploit

The vulnerability is very easy to exploit.
```bash
curl -v -L {BaseURL}/sap/public/bc/icf/logoff?redirecturl=https://example.com
```

An HTTP redirection based on `location` HTTP header is performed. It follows the URL given in `redirecturl`

## What is the impact ?

An open redirect vulnerability can be used in phishing or social engineering attack to convince a user to click on a link that appears legitimate at first sight but ends up malicious.

When used in a phishing campaign, the two main use cases are:
- Used to target anyone by using the reputation of the site or the brand which is vulnerable to the open redirect
- Used as an advanced phishing method to attack the company behind the site vulnerable to the open redirect

## How to fix ?

Configure the application with a whitelist of allowed redirect URL.

Documentation:
- https://userapps.support.sap.com/sap/support/knowledge/en/3143650
- https://wiki.scn.sap.com/wiki/display/ABAPConn/The+logoff+parameter+redirecturl+is+marked+as+a+security+vulnerability

## Links

- https://userapps.support.sap.com/sap/support/knowledge/en/3143650
- https://wiki.scn.sap.com/wiki/display/ABAPConn/The+logoff+parameter+redirecturl+is+marked+as+a+security+vulnerability
- https://cwe.mitre.org/data/definitions/601.html

## License

[MIT License](https://opensource.org/licenses/MIT) © [ndmalc]