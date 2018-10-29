# NodeJS
NodeJS is a JavaScript runtime built on Google's V8 engine. It is great for creating web/application servers. It uses npm as its package manager.

#### The typical modules used are:
- express (web server route manager & configurator)
- passport (security layer)
- mssql (sql server client using the Tedious driver)
- express-session (session middleware)
- http(s) (the web server)
- socket.io (for realtime apps)

### Goals

NodeJS should:

 - Serve images as a static directory
 - Never have unhandled exceptions. Everything should use .then -> .catch
 - Use middleware for endpoint security
 - Set CORS through express use()
 - Keep data interfacing API as an importable module
 - Listen on a unique port if running on cliffjumper
 - Be aware of callback hell http://callbackhell.com/

### Getting Started with NodeJS

Get the installer here:
https://nodejs.org/en/download/
If on OSX, install via homebrew

Then read the documentation:
https://nodejs.org/docs/latest-v9.x/api/synopsis.html
##### Selection of Third Party Code


Selection of a library or framework is never an easy task. Things that should be considered include:

- Is it on GitHub? Is it a package in NPM? If it isn't, don't use it.
- When was the last commit date? Was it more than a year ago?
- How many commits has this project had?
- How many contributors are there to this project? Maintainers? Do they take care of the project's issues?
- How many stars does this project have?
- How much of this project is actually needed?
- What is its license? Please refrain from Copyrighted and AGPL libraries as much as possible.
- Always install packages using --save


Sample project directory

```markup
├── app/
│   ├──  index.js
│   ├──  api/
|   │    ├── separatejs
|   │    │── route.js
|   │    ├── logic.js
|   │    ├── whenItMakesSenseTo.js
|   │    ── ...
```
