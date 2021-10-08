# express-async-catch

Simple wrapper for Express route handlers, which propagates errors to the centralized error handler.

## Install

```bash
npm install express-async-catch
```

## Usage

Import the wrapper function:

```js
const asyncCatch = require('express-async-catch');
```

Wrap your route handlers:

```js
app.get('/api/product/list', asyncCatch(async (req, res, next) => {
    // ...
  })
);
```

## Notes
* This wrapper will catch both thrown Errors.
* This wrapper will catch promise rejections, when the await keyword is used.
* It cannot catch errors that generated un-awaited promises.
* It cannot catch errors that are handled via callbacks.
* It cannot be used to wrap the error handler (signature err, req, res, next) 
  because it expects the wrapped route handler to have the signature (req, res) or (req, res, next).
