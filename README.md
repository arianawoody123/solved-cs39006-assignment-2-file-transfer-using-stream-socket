Download Link: https://assignmentchef.com/product/solved-cs39006-assignment-2-file-transfer-using-stream-socket
<br>
<strong>Objective: </strong>

The objective of this assignment is to get familiar with stream sockets (also called TCP sockets) using POSIX C programming. A stream socket establishes a connection between the client and server, which remains there until one of them closes it (explicitly or implicitly on exit). The connection can be used to transfer ordered sequence of bytes between two computers (processes) reliably.




<strong>Problem Statement:</strong>

Your task will be to write two programs – one program corresponding to the server process and another program corresponding to the client process. As in Assignment 1, the client process requests for the content of a file (by providing the file name) and the server process sends the contents of that file to the client. The file is a text file of <strong><em>arbitrary size</em></strong> (&gt; 0 bytes).




The transfer of the contents of the file works using a communication protocol as follows.

<ol>

 <li>The client establishes a connection to the server using the connect() call.</li>

 <li>The client reads the filename from the user (keyboard).</li>

 <li>The client sends the file name to the server. You can assume that the length of the filename is less than 100 characters.</li>

 <li>The server looks for the file in the local directory, if the file is not there it closes the connection without sending anything. The client needs to detect this and print an error message “File Not Found” and exit.</li>

 <li>If the file is present, the server reads the contents of the file and sends it to the client. Since the file can be arbitrarily long, the server cannot send the entire file in a single send() call, and sends the file in small chunks using multiple send() calls until the entire file is transferred. The chunk size used by the server is not known to the client. The server closes the connection after sending the entire file.</li>

 <li>The client reads the file contents sent by the server and copies it into a new file in the current directory (so you need to run the server and the client from different directories to avoid overwriting the same file that the server is reading). The client also maintains a running count of the number of bytes and the number of words in the file. For the purpose of this assignment, you can take ‘,’ (comma), ‘;’ (semicolon), ‘:’ (colon), ‘.’ (fullstop), or one or more whitespace (space/tab), or any combinations of them, as delimiters between two words. For example, “this is”, “this is”,  “this,is”, “this,   is”, “this,,   ; is” are all to be taken as 2 words).</li>

 <li>After the entire file is transferred, the client prints a message “The file transfer is successful. Size of the file = X bytes, no. of words = Y”, where X is the no. of bytes in the file and Y is the number of words in the file.</li>

</ol>




<strong><em>You need to ensure the following in your code</em></strong>:

<ol>

 <li>No buffer of size &gt; 100 can be used in either client or server.</li>

 <li>The server cannot make more than one pass over the file, nor can it find the size of the file in any other way.</li>

 <li>The client cannot read the file. It can only write to the file.</li>

 <li>You cannot use fopen/fscanf/fprintf functions. You must use open/read/write functions to read/write from/to the file.</li>

</ol>




<strong>Submission Instruction: </strong>

You should write two C programs – file_server.c (contains the server program) and file_client.c (contains the client program). Keep these two files in a single compressed folder (zip or tar.gz) having the name &lt;roll number&gt;_Assignment2.zip or &lt;roll number&gt;_Assignment2.tar.gz. Upload this compressed folder at Moodle course page by the deadline.