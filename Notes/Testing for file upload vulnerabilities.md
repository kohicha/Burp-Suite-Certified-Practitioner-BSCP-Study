---
Title: Testing for file upload vulnerabilities
tags:
  - File-Upload
---
File upload vulnerabilities occur whenever there is a lack of validation on a file upload feature, whether it is the file size, file contents, file name, etc.

A file upload vulnerability can have different scenarios, for example, if the server handles uploaded files and executes them, an attacker could escalate that  and turn it into a web shell or access arbitrary commands. Or they could upload a file with the same name as the existing file and overwrite the original file.

