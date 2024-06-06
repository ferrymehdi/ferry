# Ferry
Simple express middleware for server-side routing with React.

```
npm install ferry
```

# Usage
##1. Call `ferry.route` with your configuration in the express `app.use` function to use ferry as middleware.
```js
var Main = React.createFactory(require('./app/components/Main'));
var ferry = require('./ferry.js');
var app = express();

app.use(ferry.route({ /* config options */ }));
```

### ferry.route options
`ferry.route` accepts an options object, with 3 required parameters:
- `parentComponentFactory` is a React factory.
- `htmlPath` is the file path of the layout HTML file.
- `routes` is a JSON array of route objects consisting of a `path` and `componentFactory`.
```js
app.use(ferry.route({
    parentComponentFactory: Main,
    htmlPath: __dirname + '/public/layout.html',
    routes: [
        {
            path: '/',
            componentFactory: Home
        },
        {
            path: '/work',
            componentFactory: Work
        },
        {
            path: '/contact',
            componentFactory: Contact
        }
    ]
}));
```

##2. Put "ferryTemplate" (without quotes) in the your HTML file. Ferry replaces this string with the HTML generated by your react component factory.
```html
<!-- ... -->
<body>
    <div style="width:100%;height:100%;">
        ferryTemplate
    </div> 
</body>
<!-- ... -->
```

# Running tests
`npm test`
