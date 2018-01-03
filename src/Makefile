#Makefile

make: ftpclient.c ftpserver.c
	gcc -pthread -g -Wall ftpclient.c -o ftpclient
	mv ftpclient ../bin
	gcc -g -Wall ftpserver.c -o ftpserver
	mv ftpserver ../bin

clean:
	rm ../bin/ftpclient ../bin/ftpserver