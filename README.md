# enchilada

serve up your javascript files all wrapped up. Yum!

```javascript
var app = express();

// serves up all your javascript files, handling all require() calls
app.use(enchilada(__dirname + '/public'));

// fallback for other static resources
app.use(express.static(__dirname + '/public'));
```

## with ingredients

No one likes a stale enchilada. Out in the real world, you want to leverage browser caching for rarely changing files.

Just add the proper ingredients and your enchilada will be served up as you requested.

```javascript
app.use(enchilada({
    src: __dirname + '/public',
    routes: {
        // key is the url route, value is either a file under src or a module
        '/js/jquery.js': '/js/jquery.js',
        // here we serve up a module
        '/js/engine.io.js': 'engine.io-client'
    }
});
```

## install

Install with [npm](https://npmjs.org)

```shell
npm install enchilada
```