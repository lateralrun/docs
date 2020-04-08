# Cloud Functions

The Lateral.run code editor allows your customers to write JavaScript that's
executed in a Node.js v12 runtime. We call these _Cloud Functions_.

## Code

We purposely tried to keep the conventions as normal as possible here, so that
your customers don't have to learn lots of Lateral.run nuances to get started.

There are just a few things to be aware of:

- `data` is an object containing the values passed by the app. There's no need
  to declare or important this variable – it's just available.
- A `return` statement passes data back to the app (which it may or may not
  use). Any value that can be converted to JSON is valid, such as an object,
  string, number, or boolean. If no `return` statement is used, the value passed
  back is `undefined`.
- There's no need to export the code with `module.exports` or the like. We
  handle that behind-the-scenes.

## Dependencies

If the package can be installed publicly via npm, then it's available to use.
Built-in Node.js modules, such as `querystring`, are also available.

## Variables

Variables are great for storing configuration values outside of the code, and
they're fully encrypted to keep any secrets safe. They're accessed through
`process.env.{{NAME}}`, which is the standard way of accessing environment
variables in Node.js.

## Run

Your customers can test the code they've written by manually running it through
the Lateral.run code editor. If you've provided example data for the event, then
it's automatically populated as the request, and your customers can quickly
tweak or keep as-is.

## Logs

Anything logged to the `console` is available for review and debugging. Uncaught
errors are automatically logged as well.

## Limits

- 128 MB of memory
- 10 seconds of execution time
- 512 MB of `/tmp` storage
- 250 MB of code / dependencies
- 256 KB (async) / 6 MB (sync) of data
- 4 KB of variables
