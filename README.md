hulken_informant_hapi8
=========================

an informant for the stress test tool [hulken](https://github.com/hellgrenj/hulken) (works with hapi.js 8).  
this small module inspects your routes and generates a hulken requests file automatically.

## Installation

`npm install hulken_informant_hapi8 --save`
## Usage

```
var Hapi = require('hapi');
var server = new Hapi.Server();
server.connection({ port: 8686});


// SET UP ROUTES HERE


var hulkenInformant = require('hulken_informant_hapi8');
var silentOnSuccess = true;
hulkenInformant.generateHulkenRequestsFile(‘./hulkenRequestsFile.json’, server, silentOnSuccess);
```
an hulken_informant offers a quick and simple way to create a stress test suite by inspecting your application routes and auto generating the requests file for you!

It has, however, it’s drawbacks:
* It can only include GETs (it has no way of figuring out what payload to send with the POST etc.)
* It can not offer an expectedTextToExist value for each request, leaving Hulken with only the HTTP status code to rely on when verifying responses.
