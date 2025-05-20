---
Title: File path traversal, traversal sequences stripped with superfluous URL-decode
tags:
  - Labs
  - path-traversal
---
1. Intercept an image query request
![[Pasted image 20250520161902.png]]
2. Most of the payloads we've used before are rather ineffective, looking back at the lab description, *The application blocks input containing path traversal sequences. It then performs a URL-decode of the input before using it.*
> [!Understanding]
> In order to truly understand what's happening under the hood, let's break it down 1 by 1.
> 1. The application blocks input containing path traversal sequences
> 2. It then performs a url-decode of the input before using it.
> 
> Before we proceed, here's the application flow if we send a url-encoded payload without the process above: 
> url-encoded payload -> application decodes this payload (system path interpretation) -> executes the payload
> 
> Now, if we add the application flow which performs an initial url-decode before using the current payload, it will look like this:
> url-encoded payload -> check for traversal -> application url-decode (added by developer) ->  application url-decode (system path interpretation) -> executes the payload
> 
> So, in conclusion, we could use a double url-encoded payload.

![[Pasted image 20250520163604.png]]
`%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66/etc/passwd`







