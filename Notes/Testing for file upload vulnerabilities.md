---
Title: Testing for file upload vulnerabilities
tags:
  - File-Upload
---
File upload vulnerabilities occur whenever there is a lack of validation on a file upload feature, whether it is the file size, file contents, file name, etc.

A file upload vulnerability can have different scenarios, for example, if the server handles uploaded files and executes them, an attacker could escalate that  and turn it into a web shell or access arbitrary commands. Or they could upload a file with the same name as the existing file and overwrite the original file.

# Content-Type Bypass
Whenever you upload a file, the application first interprets what type of file you are uploading, for example, if you upload an image, the content-type would be `image/*` or `image/png` etc. Now if you upload a larger file, it would resort to using `multipart/form-data` where there are multiple parts of data from the file. 

> [!Example Scenario]
> You can check whether or not the server validates the Original Content-type of the file you are uploading, for example, you uploaded an image, but then you change the contents and file name of it to `.php`, and the server still executes the file as if it was a .php file. Read [[Web shell upload via Content-Type restriction bypass]].

# Uploading the file to another directory
Now, we can actually try and chain some vulnerabilities when trying to exploit file upload vulnerabilities. We can use path traversal, to upload the file to another directory. This is because there is no sanitation function that is implemented or working on the server side of the application, in which can be exploited by the attacker. [[Web shell upload via path traversal|Read]]

# Blacklisting file-types
Blacklisting file-types can prevent arbitrary extensions, well, not all of it. In some servers, like Apache, we can try and override their default configuration in the same directory. [[Web shell upload via extension blacklist bypass|Read]]. We can also try to bypass these, by using obfuscation techniques, e.g `.jpg.php` or `.p.phphp`. An example of that is using a [[Web shell upload via obfuscated file extension|null byte `%00`]].

