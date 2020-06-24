import socket

from http.server import HTTPServer, BaseHTTPRequestHandler

''' 

This main function is for to define the port for server
and also create a socket

'''
def main():
    
    PORT = 8000
    server_address = ('localhost', PORT)
    server = HTTPServer(server_address, requestHandler)
    serversocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    print ('Server running on port %s' % PORT)
    server.serve_forever()
    serversocket.listen(1) 

    
'''

From line 32 to line 259

A client makes connection request to the server.
The server sends a response to the client telling the client how to proceed.
The client can view resources if he/she wishes.

'''

class requestHandler(BaseHTTPRequestHandler):


#Request client to continue or not

    def do_GET(self):
        if self.path.endswith('/Client'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
        
            output = ''
            output += '<html><body>'
            output += '<h1> Assignment 4 EKT434 </h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '<h2> Do you want to continue? Yes or No </h2>'
            output += '<h3><a href="/Client/Yes">Yes</a></h3>'
            output += '<h3><a href="/Client/No">No</a></h3>'
            output += '</br>'
            output += '<body><html>'
            self.wfile.write(output.encode())
         
#Request client to choose either downloading or streaming
          
        if self.path.endswith('/Yes'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h3><a href="/Client/Yes/Downloading">1. Downloading</a></h3>'
            output += '<h3><a href="/Client/Yes/Streaming">2. Streaming</a></h3>'
            output += '</br>'
            output += '<body><html>'
            self.wfile.write(output.encode())

#If client choose downloading, the server will list the resource for client to chooose
        
        if self.path.endswith('/Downloading'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceA">1. Resource A (Document Files)</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceB">2. Resource B (Image Files)</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceC">3. Resource C (Live Video & Multimedia Files)</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceD">4. Resource D (Compressed Files)</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceE">5. Resource E </a></h3>'
            output += '</br>'
            output += '<p>Please select your resource for Downloading :<p>'
            output += '<body><html>'
            self.wfile.write(output.encode())

#If client choose streaming, the server will list the resource for client to chooose
        
        if self.path.endswith('/Streaming'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h3><a href="/Client/Yes/Streaming/ResourceC">1. Resource C (Live Video & Multimedia Files)</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
            
#For resource A (Document Files)

        if self.path.endswith('/ResourceA'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h2>Document Files</h2>'    
            output += '</br>'            
            output += '<h3><a href="Assignment4.pdf" > Download Assignment4.pdf file </a>'
            output += '</br>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceA/ToContinue">1. To Continue</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceA/Exit">2. Exit</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
                       
#For resource B (Image Files)
          
        if self.path.endswith('/ResourceB'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434 HTTP Server</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<p>Click on the UniMAP Logo to download the image:<p>'
            output += '<a href="https://www.unimap.edu.my/images/headers/LogoUniMAP2017.png" download>'
            output += '<img src="https://www.unimap.edu.my/images/headers/LogoUniMAP2017.png" width="250" height="190">'
            output += '</a>' 
            output += '</br>'           
            output += '<h3><a href="/Client/Yes/Downloading/ResourceB/ToContinue">1. To Continue</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceB/Exit">2. Exit</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
            
#For resource C (Live Video & Multimedia Files)
            
        if self.path.endswith('/ResourceC'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<iframe width="1519" height="598" src="https://www.youtube.com/embed/u_5capGaYS4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>'
            output += '</video>'
            output += '</br>'
            output += '<h3><a href="/Client/Yes/Streaming/ResourceC/ToContinue">1. To Continue</a></h3>'
            output += '<h3><a href="/Client/Yes/Streaming/ResourceC/Exit">2. Exit</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
            
#For resource D (Compressed Files)
        
        if self.path.endswith('/ResourceD'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h3><a href="Assignment4.rar" > Download Assignment4.rar file </a>'
            output += '</br>'          
            output += '<h3><a href="/Client/Yes/Downloading/ResourceD/ToContinue">1. To Continue</a></h3>'
            output += '<h3><a href="/Client/Yes/Downloading/ResourceD/Exit">2. Exit</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
        
#For resource E
  
        if self.path.endswith('/ResourceE'):
            self.send_response(404)
            self.send_header('content-type', 'text/html')
            self.end_headers()
            
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h2>404 Not Found</h2>'
            output += '<body><html>'
            self.wfile.write(output.encode())

#Codes for client if wants to continue       
       
        if self.path.endswith('/ToContinue'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
        
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h2>Do you want to continue? Yes or No</h2>'
            output += '<h3><a href="/Client/Yes/ToContinue/Yes">Yes</a></h3>'
            output += '<h3><a href="/Client/Yes/ToContinue/No">No</a></h3>'
            output += '</br>'
            output += '<body><html>'
            self.wfile.write(output.encode())  


#Codes for client if does not wants to continue
  

        if self.path.endswith('/No'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
        
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '<h3><a href="/Client/Yes/ToContinue/No/Exit">Exit</a></h3>'
            output += '<body><html>'
            self.wfile.write(output.encode())
                                

#Codes for client if wants to exit 
  
        if self.path.endswith('/Exit'):
            self.send_response(200)
            self.send_header('content-type', 'text/html')
            self.end_headers()
        
            output = ''
            output += '<html><body>'
            output += '<h1>Assignment 4 EKT434</h1>'
            output += '<h1> HTTP Client-Server Download & Video Streaming Centre Using Socket Programming </h1>'
            output += '</br>'
            output += '<h2>Bye!</h2>'
            output += '<body><html>'
            self.wfile.write(output.encode())
            
'''

To execute code only if the file was run directly, and not imported.

''' 

if __name__ == '__main__':
    main()
