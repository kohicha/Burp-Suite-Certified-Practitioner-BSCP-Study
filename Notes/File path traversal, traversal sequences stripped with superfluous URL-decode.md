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
> what we could do, is 







