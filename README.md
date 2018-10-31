# Language study

test

## 1. Javascript

* * *

### 1.1.1. ES6

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

₩₩₩

        <!DOCTYPE html>
        <html>
            <head>
                <script data-require="traceur@*" data-semver="0.0.0-20140302" src="https://traceur-compiler.googlecode.com/git/bin/traceur.js"></script>
                <script data-require="traceur@*" data-semver="0.0.0-20140302" src="https://traceur-compiler.googlecode.com/git/src/bootstrap.js"></script>
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

₩₩₩

    1. change source code
step by step

### 1.1.1. Javascript overview

## 2. Node JS

* * *

