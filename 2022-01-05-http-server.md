title: http-server.md
==========
date: 2022-01-05 13:50
tags: []
categories: []
- - -

```js
const http = require('http');
const fs = require('fs');
const port = 3000;
const globalSetup = () => {
  const server = http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    fs.readFile('dist/index.html', (error, data) => {
      if (error) {
        res.writeHead(404);
        res.write('Error: File not found');
      } else {
        res.write(data);
      }
      res.end();
    });
  });
  server.listen(port, (error) => {
    if (error) {
      console.log('Some error', error);
    } else {
    console.log(`Server running at ${port}/`);
    }
  });
}

module.exports = globalSetup;
```
