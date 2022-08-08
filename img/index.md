# Image API  
  
There are three main endpoints in the `/img` section.  
  
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
# Image Fetch
## Relative Link:
`/img/<image_id>/`
## Description
Used to fetch an image from the Compensation API.
You can use the `base64` query parameter to fetch in a base-64 encoded format instead of a standard one.

## Example Request - Standard
```
URL:
https://api.compensationvr.tk/img/0/

Headers: N/A
Body: N/A
```
## Example Response - Standard
<img src="https://api.compensationvr.tk/img/1/">

## Example Request - Base64
```
URL:
https://api.compensationvr.tk/img/1?base64=true

Headers: N/A
Body: N/A
```
# Image Metadata Fetch
## Relative Link:
`/img/<image_id>/info`
## Description
Used to fetch image metadata from the Compensation API.
All data is JSON-formatted.

## Example Request
```
URL:
https://api.compensationvr.tk/img/1/info

Headers: N/A
Body: N/A
```
## Example Response
```json
{
  "_id": 1,
  "internalPathRef": "images/1.jpg",
  "takenBy": {
    "id": "2",
    "nickname": "Raven",
    "username": "Raven"
  },
  "takenInRoomId": "0",
  "others": [],
  "room": {
    "id": "0",
    "creator": "0",
    "name": "Apartment"
  },
  "infoPath": "/img/1/info",
  "filePath": "/img/1",
  "takenOn": {
    "unixTimestamp": 1657232966511,
    "humanReadable": "Thu, 07 Jul 2022 22:29:26 GMT"
  },
  "social": {
    "comments": [],
    "votes": 0,
    "tags": [
      "photo"
    ]
  }
}
```