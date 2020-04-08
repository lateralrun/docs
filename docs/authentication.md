# Authentication

_Note: If you're using the [Node.js client](https://github.com/lateralrun/node),
authentication is handled for you. You can safely skip this section._

Lateral.run uses JSON Web Tokens (JWTs) for authentication between your app and
our service. Check out [JWT.io](https://jwt.io/) to learn more about JWTs,
including a helpful debugger and list of libraries for different languages and
frameworks.

## Structure

When your app wants to communicate with Lateral.run – such as embedding the code
editor in your frontend, or running your customer's code from your backend – it
should generate a JWT with the following structure:

### Header

```js
{
  "alg": "HS256",
  "typ": "JWT"
}
```

### Payload

```js
{
  "iss": "{{YOUR_APP_ID}}",
  "sub": "{{ACCOUNT_ID}}",
  "iat": "{{UNIX_TIMESTAMP}}",
  "exp": "{{UNIX_TIMESTAMP}}"
}
```

- `sub` ensures the token can only be used to access resources belonging to the
  specified account (i.e., your customer).
- `exp` should be a timespan you're comfortable with relative to `iat`. For
  example, the [Node.js client](https://github.com/lateralrun/node) defaults to
  30 seconds for API requests (since it generates a new one for every request)
  and 24 hours when embedding the code editor.

### Secret

Use the secret we generated for your app to sign the token.

## Handoff

The JWT you generate should be passed in a request header:

```
Authorization: Bearer {{TOKEN}}
```

The sole exception to this is embedding the code editor in your frontend, which,
by its nature as an `iframe`, does not allow custom headers to be set. Instead,
the JWT should be passed through the query string:

```html
<iframe src="https://app.lateral.run/editor?token={{TOKEN}}" />
```
