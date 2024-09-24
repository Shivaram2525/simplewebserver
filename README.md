
# EX01 Developing a Simple Webserver
## Date: 24-09-2024
# Name: Shivaram M.
# Reg.No.: 212223040195

## AIM:
Develop a webserver to display the configuration details of your laptop.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```

import platform
from http.server import HTTPServer,BaseHTTPRequestHandler

system_name = platform.system()
node_name = platform.node()
release = platform.release()
version = platform.version()
machine = platform.machine()
processor = platform.processor()

content='''
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My System Configuration</title>
</head>
<body>
    <h1>My System Configuration</h1>
    <ul>
        <li>'''+system_name+'''</li>
        <li>'''+node_name+'''</li>
        <li>'''+release+'''</li>  
        <li>'''+version+'''</li>  
        <li>'''+machine+'''</li>  
        <li>'''+processor+'''</li>  
    </ul>
</body>
</html>
'''

class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200) 
        self.send_header("content-type", "text/html")       
        self.end_headers()
        self.wfile.write(content.encode())

print("This is my webserver") 
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()

```


## OUTPUT:
![Web_Exp_1(1)](https://github.com/user-attachments/assets/17b9c8cd-2fbc-40f2-85c6-5e4427c8c809)
![Web_Exp_1(2)](https://github.com/user-attachments/assets/9b53ce39-94ff-4b16-9e63-19915a1f2798)



## RESULT:
The program for implementing simple webserver is executed successfully.
