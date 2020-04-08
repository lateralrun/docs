# Integration: Frontend

To integrate the Lateral.run code editor into your frontend, simply embed an
`iframe` where you want it to display:

```html
<iframe src="https://app.lateral.run/editor?token={{TOKEN}}" />
```

See [Authentication](docs/authentication.md) for instructions on building the
token.

## Node.js

If you're using the [Node.js client](https://github.com/lateralrun/node), you
can generate the URL (including token) with the following code:

```js
const Lateral = require('lateralrun')

const lateral = new Lateral({
  appID: '{{YOUR_APP_ID}}',
  appSecret: '{{YOUR_APP_SECRET}}',
})

const editorURL = lateral.generateEditorURL({ account: 12345 })
```

## Sizing

Feel free to size the `iframe` to fit within your app. The code editor is
responsive and should fit within most spaces.

## Rendering Considerations

If your app renders on the server-side, the URL/token can be generated and
passed through to the template just as you would any variable.

If you run a SPA or JAMstack app, you can generate the URL/token and pass it
through a new or existing API endpoint for your frontend to consume.

Either way, ensure that the token expiration is long enough for a typical
session, and/or build in a mechanism to refresh the page/token before it
expires.
