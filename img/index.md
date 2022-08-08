# Image API  
  
There are two main endpoints in the `/img` section.  
  
# Image Upload  
## Relative link:  
`/img/upload`  
## Description  
Used to upload an image to the Compensation API servers.  
Images must be Base64 encoded then placed in the body of the request.  
Multiple query parameters are required:  
  
<ul>
    <li>room_id</li>
    <li>others</li>
    <li>tags</li>
</ul>
  
## Example Request  
  
```  
URL:  
https://api.compensationvr.tk/img/upload?room_id=<room_id>&others=["1", "0"]&tags=["test"]  
  
Headers:  
Content-Type: text/plain  
Content-Length: <length>  
Authentication: Bearer <auth token>  
  
Body:  
<Base 64 encoded image>  
```  