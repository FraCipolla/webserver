# webserver
A functional C++ webserver

In this project we coded a simple webserver using poll() to handle multiple connection. The main server accepts new connections, read from clients sockets, than redirect the request to the proper virtual server.

Poll() is a bit tricky, there's not only 1 way to implement it so we decided to always go back to poll after every recv() and let the poll decided the sockets priority. When the server recv a full request we procede to pass it to the target virtual server.

After a request is completed, we send the response and close the client socket. We implemented a sort of cache to speed up the server, storing into a map every new different request and the corresponding answer.

This webserver can handle GET, HEAD, POST, PUT and DELETE method. It can handle uploads as well, from content-type requests and chunk-encoding.

The attached tester test over 5000 requests sended from 20 clients simultaneously, 10gb of upload from different CGI requests, 128 clients simultaneously and more.
