# Content-Security-Policy Level Nonces

### CSP Nonces

- Checkout Branch `csp-nonces` (`git checkout csp-nonces`)
- Since we now also implement a server we have new dependencies inside the `package.json` (you need to run `npm install` again)
- Make sure the XSS attack takes place so we know we mitigate it with the CSP Header
- Now we need to configure our CSP Nonces on the server:
- Insert the Angular 'ngCspNonce'-Attribute to the `app-root`-HTML Tag and set the Value to 'myRandomNonce'
- Open the `server.js`-File and set the Content-Security-Policy we have used previously. But this time insert the calculated `nonce`-Value inside the `script-src`-Attribute instead of an Hash-Value

### Hints

```javascript
//server.js
const modifiedHtml = data.replace(/myRandomNonce/g, nonce);
...
res.setHeader(
  "Content-Security-Policy",
  `default-src 'none'; script-src 'self' 'nonce-${nonce}'; connect-src 'self' http://localhost:4730; img-src 'self'; style-src 'self' 'unsafe-inline';`
);
```

```html
<app-root ngCspNonce="myRandomNonce"></app-root>
```

[Solution](https://github.com/martinakraus/angular-security-2026/tree/csp-nonces-solution)
