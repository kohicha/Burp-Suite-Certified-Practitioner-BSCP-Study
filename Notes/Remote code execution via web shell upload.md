---
Title: Remote code execution via web shell upload
tags:
  - Labs
  - File-Upload
---
1. Upload and intercept the POST request on the avatar upload feature
![[Pasted image 20250522134538.png]]
2. Replace the original content of the POST request with a php webshell, and replace the file name with a `.php` extension.
![[Pasted image 20250522134947.png]]
3. Access the file to get the secret.
![[Pasted image 20250522135025.png]]








