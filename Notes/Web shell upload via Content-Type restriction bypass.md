---
Title: Web shell upload via Content-Type restriction bypass
tags:
  - Labs
  - File-Upload
---
1. Upload and intercept an avatar upload POST request
![[Pasted image 20250522141124.png]]
2. We can see that there is a content-type header on the form data, let's change that to `application/x-httpd-php` and the content with a php script that gets the file contents of `/home/carlos/secret`
![[Pasted image 20250522141626.png]]
That doesn't work, and the errors return that we can only use `image/jpeg` and `image/png`.
3. Instead, we'll just change the contents of the file and the file name, as the server does not do a validation of the file content and file name.
![[Pasted image 20250522142137.png]]
4. Get that secret!
![[Pasted image 20250522142203.png]]
