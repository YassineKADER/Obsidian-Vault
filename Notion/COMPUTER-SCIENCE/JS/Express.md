```JavaScript
npm init -y
npm install express
```

## Start the server

```JavaScript
node main.js
```

## To setup the developement kit:

```Diff
    "scripts": {
+     "start": "node app.js"
    },

//to run it:
npm start
```

### Nodemon:

```JavaScript
npm install nodemon --save-dev

"scripts": {
+     "dev": "nodemon app.js",
      "start": "node app.js"
    },

//to runit
npm run dev
```