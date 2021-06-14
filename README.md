# set up:
```npm i cors-anywhere```

1. create a folder called (or whatever you want)```server``` add a file ```server.js``` and add the following code
```
// Listen on a specific host via the HOST environment variable
var host = process.env.HOST || '0.0.0.0';
// Listen on a specific port via the PORT environment variable
var port = process.env.PORT || 8080;

var cors_proxy = require('cors-anywhere');
cors_proxy.createServer({
    originWhitelist: [], // Allow all origins
    requireHeader: ['origin', 'x-requested-with'],
    removeHeaders: ['cookie', 'cookie2']
}).listen(port, host, function() {
    console.log('Running CORS Anywhere on ' + host + ':' + port);
});
```

2. add to the package json a script to run the server 
```"cors-server" : "node server/server.js"```

# how to use:

start the server ```npm run cors-server ``` and add ```http://localhost:8080/``` before the url you need the cors to be fixed in your front-end project

example :
```
let url = 'http://localhost:8080/https://notmystoreyet.myshopify.com/admin/api/2021-04/products.json'
```

then do your regular fetch, axios etc call to get the response.
