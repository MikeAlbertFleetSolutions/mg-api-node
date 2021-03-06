# mg-api-node

Unofficial nodejs client for the MyGeotab API

### Getting Started

```sh
npm install mg-api-node --save
```

### Usage

```js
var api = new API(userName, password, database);

api.authenticate(function(err, data) {
  if (err) {
    console.log("Error", err);
    return;
  }

  api.call(
    "Get",
    {
      typeName: "User",
      search: {
        name: data.userName
      }
    },
    function(err, data) {
      if (err) {
        console.log("Error", err);
        return;
      }
      console.log("User", data);
    }
  );
});
```

#### Session ID

It's also possible to supply session ID and direct server to re-use a session ID. This avoids costly authentication.

```js
var api = new API(userName, password, database, server, options, sessionId);

api.call(
  "Get",
  {
    typeName: "User",
    resultsLimit: 1
  },
  function(err, data) {
    if (err) {
      console.log("Error", err);
      return;
    }
    console.log("User", data);
  }
);
```

### Running Tests

```sh
npm install -g mocha
npm install
mocha
```
