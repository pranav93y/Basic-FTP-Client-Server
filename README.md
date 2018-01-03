

# Basic FTP Client/Server
This was one of my assignments for CMPE156 Network Programming that provides two utilities, client and server, to allow the user remote access between them using the Berkeley sockets library in C. This project consists mainly of;
- "ftpclient.c", C source file for the client program
- "ftpserver.c", C source file for the server program
- "Makefile", make utility to complile the soucre files into executables

The sources files are located in the src directory, and the compiled executables are located in the bin directory. The test directory contains ebooks in text format obtained from [http://www.gutenberg.org/](http://www.gutenberg.org/), used as test files for the project. 

*NOTE: The client and server executable files should be located different directories*


# Usage
- Server
```
./ftpserver <listen-port>
```

- Client
```
./ftpclient <server-ip> <server-listen-port>
```

# Interface Commands
This is a really basic client utility which can perform 4 different functionalities;

- ls, lists the current directory
- get <filename>, gets the file from server to client
- put <filename>, puts the files from the client to the server
- quit, exits the client program

*NOTE: The server program will keep running even after a client has been disconnected, waiting for future connections*

*NOTE: The provided client and server utilities do not include directory changing functionalities*

# Example Run
- The console on the left is running the ftpclient, which currently does not contain other files in its directory. 
- The console on the right is running the ftpserver, which contans the test files in its directory. 


![Imgur](https://imgur.com/a/egHQy.gif)

