# restaurant-management-system

## Project setup

```
npm install
```

## Install JSON Server
```
npm install -g json-server
```

### Create a db.json file with some data
```
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Install JSON Server
```
npm install -g json-server
```

### Start JSON Server

```
json-server --watch db.json
```

### Compiles and minifies for production

```
npm run build
```

#### Now if you go to http://localhost:3000/posts/1, you'll get (example)

```
{ "id": 1, "title": "json-server", "author": "typicode" }
```

### Lints and fixes files

```
npm run lint
```

### Learn more about JSON Server
[JSON Server Getting Started](https://www.npmjs.com/package/json-server#getting-started)

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
