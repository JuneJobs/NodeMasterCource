# Language study

test

## 1. Javascript

* * *

### 1.1. ES6

 **ES6** is not working on some browser. So We need to setup the helper.

    1. Go to Plunker site([https://github.com](http://plunker.co)) -> Editor
    2. Go to html page -> Refresher
    3. Install helper ES6 like below.
    4. Traceur (Convert ES5 to ES6)
        * Click book icon and search traceur.
        * Click magic stick icon in result panel.
    5. Install Systemjs
        * Same as Traceur
    6. Generated code should be like below.

```html
<!DOCTYPE html>
    <html>
        <head>
            <script data-require="traceur@*" data-semver="0.0.0-20140302" src="https://traceur-compiler.googlecode.com/git/bin/traceur.js"></script>
            <script data-require="systemjs@*" data-semver="0.21.4" src="//cdnjs.cloudflare.com/ajax/libs/systemjs/0.21.4/system.js"></script>
            <script src="https://google.github.io/traceur-compiler/bin/traceur.js"></script>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.18.2/system.js"></script>
            <script type="text/javascript">
            System.import('./app.js');
            </script>
        </head>
        <body>
            <div id="main">
                <h1>test</h1>
            </div>
        </body>
    </html>
```

    7. change source code (traceur-compiler.googlecode.com/git) to (google.github.io/traceur-compiler)
    8. Add following script in head

```html
    <script type="text/javascript">
      System.import('./app.js');
    </script>
```

    1. Try code on script.js file.
  
#### 1.1.1. Module

Study about the javascript module.

    1. Make an external.js file
    2. Say in external.js like below.

```javascript
    //external.js
    export let keyValue = 1000;
    export function test() {
        keyValue = 2000;
        console.log('tested!');
    }
    let db = 'Some text';
    export default db //Default should be one in a module.
    // or -> export {keyValue, test}
```

    3. Put code in app.js like below.

```javascript
    //app.js
    import a, { keyValue, test as key} from 'external.js';
    //It doesn't need key for get value. (Because of default keyword)
    import db from 'external.js';   
    from './external.js'; // Can be used like this -> from './external'
    console.log(keyValue); //1000
    test();
    console.log(key);   // test's Reference copied
    console.log(keyValue); //2000 <- Reference copied.
    console.log(a); //Default value
```

    4. If I want to import all of module, put like below.

```javascript
    //app.js
    import * as imported from 'external.js';
    console.log(imported.keyValue); //1000
    test();
    console.log(imported.keyValue); //2000 <- Reference copied.
```
Modules - Strict Mode and Global Scope
There are two important Rules, which you need to understand if you're working with ES6 Modules:

    1. Modules are always in Strict Mode (no need to define "use strict")
    2. Modules don't have a shared, global Scope. Instead each Module has its own Scope

#### 1.1.1. Javascript overview

## 2. Node JS

* * *

