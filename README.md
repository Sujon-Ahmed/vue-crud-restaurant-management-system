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

### Run json-server for storing & fetching user-info & restaurant info

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

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
