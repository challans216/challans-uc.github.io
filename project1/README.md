# WAPH-Web Application Programming and Hacking

## Instructor: Dr. Phu Phung

## Student

**Name**: Nirosha Challa

**Email**: challans@mail.uc.edu

![Nirosha Challa](images/headshot.jpg){width=150px height=150px}

# Lab 1 - Foundations of the Web

## Overview : 
This lab explores more into the web application development with front-end. As a part of Lab 1 , I understood how to analyze the network packets in a wireshark tool based on the HTTP requests and the HTTP responses with TELNET and compared them with the browser sent requests.
Within the Part 2 of Lab 1 i have learned how CGI works and done hand-ons on CGI applications in C and HTML . Apart from this PHP web application development was also covered as a part of this lab. In part 3, got familiarized with HTTP GET and POST requests using the wireshark tool and curl. After all the respective screenshots have been captured and inserted, content has been written in markdown format pandoc tool was used to generate pdf file.

[https://github.com/challans216/waph-challans/blob/main/lab/lab1/README.md](https://github.com/challans216/waph-challans/blob/main/lab/lab1/README.md)



## Part 1 : The WEB and the HTTP Protocol

### Task 1. Familiar with the Wireshark tool and HTTP protocol

Wireshark tool deals with analyzing the network packets over a network. To get familiarized with this tool I have installed it initially started the appliaction to capture the packets there i have set a filter option to any to capture all packets initially. Thereafter I started to capture the packets and fitlered by providing Http in the search box.
The Http Request consists of hostname, source and the destination ip's and the ports and the Http version. and the response consists of status code, content type ,the same source and destination ip's and ports.
The HTTP format was also captured by clicking on the response and navigating to follow http stream.

![Wireshark HTTP Request](images/Wireshark1.png)

![Wireshark HTTP Response](images/Wireshark2.png)

![Wireshark HTTP Responseformat](images/Wireshark3.png)

### Task 2. Understanding HTTP using telnet and Wireshark
Before sending an HTTP request via TELNET over the terminal to example.com or index.html, Wireshark was launched to record the network packets. First, a connection was made to the example.com web server in order to use TELNET. Using the telnet example.com portNumber syntax. The type of request, path file, http version, and host name were provided for submitting the HTTP request after the connection was made. And after pressing Enter twice, the response was obtained.
It is observed that the telnet request was missing server information when comparing the HTTP requests made through the browser with TELNET in Wireshark. Whereas the browser automatically fills in request headers like user-agent, accept, accept-language, authorization, etc., the telnet HTTP request is created manually.

![Telnet HTTP Request](images/telnet1.png)

![Telnet HTTP Request in Wireshark](images/telnet2.png)

![Telnet Repsonse in wireshark](images/telnet3.png)

![Telnet Repsonseformat in wireshark](images/telnet4.png)

## Part II - Basic Web Application Programming

### Task 1: CGI Web applications in C

a. Thorugh CGI i have developed a program in C which can print the statement as follows: "Hello World CGI! From Nirosha Challa, WAPH". This statement has been written in C by using subl. After that gcc was installed to compile the .c program. After executing the program the .cgi file has been copied to the path /usr/lib/cgi-bin. To access it on browser i have provided the localhost along with the .cgi file name which showed output on the browser as below:

![CGI in C](images/cgi.png)

b. On continuation, As a part of homework i have developed a program in C by incorporating HTML content. Here  initially i copied the helloworld.c to and index.c file and i have included the student name in the heading section and some other details in the paragraph section. In the similar way i have compiled the code with gcc and ran the program. Thenafter the .cgi was copied to the path /usr/lib/cgi-bin.To access it on browser i have provided the localhost along with the index.cgi file name which showed output on the browser as below

![CGI in C and HTML](images/CGi1.png)

Included file `helloworld.c`:
```C
    #include<stdio.h>
    int main() {
    const char *htmlContent = "<!DOCTYPE html> <html> <head> <title>Web Application Programming and Hacking</title>"
                              "</head> <body> <h1>Student: Tulasiram Nakkanaboina</h1>"
                              "<p>This exercise is done as part of Lab1 assessment i.e CGI Web Applications with C.</p></body></html>";

    printf("Content-Type: text/html\n\n");
    printf("%s", htmlContent);
    return 0;
}
```

### Task 2: A Simple PHP Web application with User input

a. PHP is a scripting language which is used for server side web application development. As a part of this task 2 i have created a simple php web application with user input. For that i have installed php and configured it with apacheserver. After that i have created a helloworld.php using subl. The sample code i have used is including helloworld and my name.It was deployed by copying it to /var/www/html and then checked on browser using the localhost address and the .php file name.

![PHP web application](images/php.png)

Included file `helloworld.php`:
```PHP
<?php
    echo "Hello World! This is my first PHP program, Tulasiram Nakkanaboina , WAPH";
?>
```

b. A PHP echo web application has been created as a aprt of homework to print the path variable that was sent with the http request. PHP's use of $_REQUEST('data') to capture the path variables in GET and POST requests is done by copying the .php file to the path /var/www/html.On the browser i provided the localhost ip address along with the filename and a ? with the user input(name).Security issues in terms of confidentiality, like SQL injections, remote code execution, and data manipulation. These hazards can be reduced by cleaning user inputs, preparing statements for SQL inputs, and performing input validation.

![PHP web application with echo](images/GET1.png)

Included file `echo.php`:
```PHP
<?php
    $inputData = $_REQUEST["data"];
    echo "The input from the request is <strong>" . $inputData . "</strong>.<br>";
?>
```

### Task 3: Understanding the HTTP GET and POST Requests
a. Here i have understood the concepts of how GET and POST requests work and analzed the packets using GET and POST call in wireshark.
Initailly HTTP GET call was performed and the path variable was provided using ? in the URL with IPaddress/echo.php?data="value".
Inplace of value user can provide a customized data. In the example i have provided my name as value. After this the HTTP request and HTTP response stream packets have been captured and analyzed. Below are the screenshots attached.

![HTTP GET request in WireShark](images/GETREquest.png)

![HTTP response in WireShark](images/GETResponse.png)

b. A command-line program called Client URL of Curl is used to process data utilizing several network protocols. I have made a post request to echo.php using CURL in the terminal.

curl -X POST localhost/echo.php -d "data=Nirosha Challa"

Here the network packets were analyzed and the HTTP stream was captured.

![HTTP POST request using CURL](images/POST.png)

![HTTP Stream in Wireshark](images/POST1.png)

c. The Similarities between GET and POST Method are
1. both are used to transfer data and upload files bewteen client and server.
2. Both use the same HTTP protocol.
3. Both methods include parameters in request.
4. HTTPS communication can be applied to both GET and POST.
Differences
1. GET is not secured since the data is exposed in the URL.
2. In POST the data is sent through request body whereas in GET it is through URL.
3. GET Url can be bookmarked whereas POST Url can't.

Since the echo.php web site is a replica of the application—that is, it simply prints the input it receives—the results from the HTTP GET and HTTP POST requests are the same.



