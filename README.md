

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