# node-client-http: Easy to make client HTTP/HTTPS request

## Fork changes
1. Allow pass proxy to request {host:"8.8.8.8", port:80}

## Feature List

1. Automatic proxy setting, if you set the proxy in your environment variable(http_proxy), it will be auto detected and used in your any HTTP request, also it will be used in your HTTPS request by HTTPS Tunnel(denpency by node-tunnel) to make HTTPS request through HTTP.

2. Make your HTTP/HTTPS request with cookie, cookie will be automatic processed int any HTTP/HTTPS request and you can get the cookie value in response.

3. HTTP redirect handling, HTTP redirect(301/302) will be automatic handled in you HTTP/HTTPS request.

## Example
    
    var http = require('client-http');

    http.get("http://www.google.com/",{host:"8.8.8.8", port:80}, function(data){
        data && console.log(data);
    });

## Installation

    git clone git://github.com/abroweb/node-client-http.git
    npm install

## Usages

### HTTPS request

    var http = require('client-http');

    http.get("https://www.google.com/",{host:"8.8.8.8", port:80}, function(data){
        data && console.log(data);
    });

### Read cookie from response

    var http = require('client-http');

    http.get("http://www.google.com/",{host:"8.8.8.8", port:80}, function(data, err, cookie){
        !err && console.log(cookie);
    });

### HTTP Post

    var http = require('client-http');

    http.request("http://www.snee.com/xml/crud/posttest.cgi",{host:"8.8.8.8", port:80}, function(data){
        data && console.log(data);
    }, "fname=hello&lname=world");

### HTTP request with custom header

    var http = require('client-http');

    // we use iPhone as our user-agent and see what happen
    http.request("http://twitter.com/",{host:"8.8.8.8", port:80}, function(data){
        data && console.log(data);
    }, null, {"User-Agent": "iPhone"});
