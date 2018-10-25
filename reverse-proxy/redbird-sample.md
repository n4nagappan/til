# A simple reverse proxy using redbird    

```
const proxy = require('redbird')({
  port: 80,
  xfwd: false,
  letsencrypt: {
    path: __dirname + '/certs',
    port: 9999,
  },
  ssl: {
    http2: true,
    port: 443,
  },
});

proxy.register('example.com', 'http://localhost:1212', {
  ssl: {
    letsencrypt: {
      email: '<email-address-here>',
      production: false,
    },
  },
});
```
