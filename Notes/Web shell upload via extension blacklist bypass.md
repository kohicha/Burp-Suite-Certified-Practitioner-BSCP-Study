---
Title: Web shell upload via extension blacklist bypass
tags:
  - Labs
  - File-Upload
---
1. Upload and intercept a POST request on the avatar upload feature
![[Pasted image 20250522153953.png]]
2. Try to upload an arbitrary php file.
![[Pasted image 20250522154103.png]]
We get php files are not allowed. Let's try to upload a file extension that CLEARLY does not exist.
![[Pasted image 20250522154152.png]]
We have successfully uploaded it, but there's a problem, the server does not execute it as a php file.
![[Pasted image 20250522154252.png]]
And since the server is running on apache, we can try and override some configurations that it has by uploading our own .htaccess file.
![[Pasted image 20250522154402.png]]

We override the default .htaccess config, and added our own application/x-httpd-php extension.
![[Pasted image 20250522154520.png]]

![[Pasted image 20250522154538.png]]
We can now visit the file, and access our arbitrary p







