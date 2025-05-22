---
Title: Remote code execution via polyglot web shell upload
tags:
  - Labs
  - File-Upload
---
1. Upload and intercept the POST request on the avatar upload feature
![[Pasted image 20250522163112.png]]
2. Let's try to change the filename and file content to a php shell and upload it.
![[Pasted image 20250522163316.png]]
we get file is not a valid image, but not something about file extensions. let's try to make a polygot file.
![[Pasted image 20250522163529.png]]
successfully uploaded.
![[Pasted image 20250522163551.png]]









