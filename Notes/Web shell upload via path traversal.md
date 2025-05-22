---
Title: Web shell upload via path traversal
tags:
  - Labs
  - File-Upload
---
1. Upload and intercept the POST request in the upload avatar feature
![[Pasted image 20250522151112.png]]
2. We'll first try to upload a php file.
![[Pasted image 20250522151224.png]]
It may have been uploaded, but the file is not being executed as a php and just returns the content of the file.
![[Pasted image 20250522151416.png]]
3. We'll try to use a path traversal vulnerability, and upload it to another directory we can ac







