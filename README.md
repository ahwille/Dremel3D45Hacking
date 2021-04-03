# Dremel 3D45 Hacking
Notes on the Dremel 3D45.   
**I have no idea if any of this violates terms of use, law or warranty. Use this information at your own risk.**

## OS
OS details: Linux 2.6.32 - 3.5

## Open Port Scan:
PORT      STATE SERVICE VERSION  
23/tcp    open  telnet  utelnetd  
80/tcp    open  http  
10123/tcp open  unknown  
10124/tcp open  unknown  

## Port 23
A telnet service. Username and password unknown at this time.

## Port 80:
Webserver runnning an HTTP API  
  
### Endpoints
  **/command**     
  Action | Data | Result | Notes
  --- | --- | --- | ---
  POST | GETPRINTERSTATUS= | You get the current status of the printer as a JSON object |
  POST | PAUSE | The current print job pauses |
  

  
  **/print_file_uploads**  
  
  POST /print_file_uploads HTTP/1.1
  Content-Type: multipart/form-data; boundary="boundary_.oOo._MzIwNDA=MTc1NTA=NjE4Nw=="
  MIME-Version: 1.0
  Content-Length: 8894816
  Connection: Keep-Alive
  Accept-Encoding: gzip, deflate
  Accept-Language: en-US,*
  User-Agent: Mozilla/5.0
  
  Used for sending g-code to printer as part of a multi-part form post.
 
## Port 10123
The video HTTP JPEG stream using MJPG-Streamer [https://github.com/jacksonliam/mjpg-streamer]

### Endpoints
  **/**  
  add the querystring ?action=stream for the live stream. example: http://10.10.10.10:10123/?action=stream  
  
  **/index.html**  
  information about the streamer applet and links
  
  **/control.html**
  Change video settings including quality and exposure
  
  **/stream.html**
  Control and view the stream
  
  
  
