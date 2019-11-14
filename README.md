

# Basic FTP Client/Server
This was one of my assignments for CMPE156 Network Programming that provides two utilities, client and server, to allow the user remote access between them using the Berkeley sockets library in C. This project consists mainly of;
- "ftpclient.c", C source file for the client program
- "ftpserver.c", C source file for the server program
- "Makefile", make utility to complile the soucre files into executables

The sources files are located in the src directory, and the compiled executables are located in the bin directory. The test directory contains ebooks in text format obtained from [http://www.gutenberg.org/](http://www.gutenberg.org/), used as test files for the project. 

*NOTE: The client and server executable files should be located different directories*

# Description
The client/server application developed as part of this project was modeled using the FTP protocol and the RFC description that defined it. The main use case for these applications is to provide functionality for remotely transferring files from a ftp server to the client application using the TCP protocol. The client application first prompts the user for input, and verifies for validity. It does this by seeing the format of the input entered, and what command the user typed. The client application accepts input with only a single whitespace. If the user entered the input with multiple whitespaces, or with other characters it does not understand, the client application will repeatedly ask the user, specifying what was wrong with the previous input. The client application also only allows a certain set of commands, and will ask the user again if they entered a command that it does not recognize. The set of commands the client application accepts are described in the Interface Commands section. 


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
- get <filename>, gets the file from server to client. The file obtained will have and appended format of “-out” at the end of the original filename.
- put <filename>, puts the files from the client to the server. The file transferred to the server will have an appended format of “-out”, similar to get.
- quit, exits the client program

*NOTE: The server program will keep running even after a client has been disconnected, waiting for future connections*

*NOTE: The provided client and server utilities can only access files within the directories containing the executables, ls however, can list the contents of directories contained within.*

# Example Run
- The console on the left is running the ftpclient, which currently does not contain other files in its directory. 
- The console on the right is running the ftpserver, which contains the test files in its directory. 
- The client firsts performs ls, prompting the server for a list of available files in its directory. 
- The client then asks to get file "a", and quits. 
- The file has been transferred from the server to the client, and has been renamed "a-out". 


![Imgur](https://imgur.com/oyjYZ36.gif)

# Design
The ftpclient and ftpserver programs use two TCP connections; control and data. The control connection is the first thing that is setup even before prompting the user for input. After it has been setup, and the user’s input has been checked for validity, the client application then sends over the PORT command, giving the server the client's ip address and the port number for the server to connect. After the data connection is setup, the client sends over the command for which the server performs and replies. After the reply is sent, the data connection is closed. The PORT command is therefore sent to the server for every new command in order to establish the data connection when needed.


