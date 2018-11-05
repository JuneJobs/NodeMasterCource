# Language study

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

    7. Change source code (traceur-compiler.googlecode.com/git) to (google.github.io/traceur-compiler)
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

#### 1.1.2. Class

Study about the javascript class

    1. The object making style like ES5

```javascript
    function Person() {
        //codes..
    }
    let person = new Person()
```

    2. The new style called Class in ES6

```javascript
    class Person() {
        greet() {   //If you want to define function, then just like this.
            console.log('hello');
        }
    }
    let person = new Person();
    person.greet();
```

    3. Define properties in Class

```javascript
    class Person() {
        constructor (name){
            this.name = name;
        }
        greet() {   //If you want to define function, then just like this.
            console.log('hello, my name is ' + this.name);
        }
    }

    let person = new Person('Max'); //Passing Name when make a new class object
    person.greet();

    console.log(person.__proto__ === Person.prototype); //true. It's pretty same which Class and Prototype.
```

    4. Inheritance

```javascript
    class Person {
        constructor (name) {
            this.name = name;
        }
        greet() {
            console.log(`Hello, my name is ${this.name} and I am ${this.age}`)
        }
    } 
    class Max extends Person {
        constructor (age) {
            super('Max'); // If child class want to use parents class's attribute, It should call parent class's constructor using super() keyword.
            this.age = age;
        }
        greetTwice() {
            super.greet(); //parent function call "Hello, my name.."
            this.greet();  //own call "hello"
        }

        greet() {
            console.log('hello');
        }
    }

    let max = new Max(27);

    max.greet();

```

    5. Static method
       It is not available use class's function like below

```javascript
    class Helper {
        logTwice(message) {
            console.log(message);
            console.log(message);
        }
    }
    Helper.logTwice('Logged!');
```

      It will shows "error" on console. But if you change the function using static like below, then you can use the function. It don't need to make object. It will be super helpful.

```javascript
    class Helper {
        static logTwice(message) {
            console.log(message);
            console.log(message);
        }
    }
    Helper.logTwice('Logged!'); // "Logged!" "Logged!"
```

    6. Getter and Setter like ES6 class style

```javascript
    class Person {
        constructor (name) {
            this._name = name;
        }
        get name () {
            return this._name.toUpperCase(); //Can make change every thing we want.
        }
        set name (value) {
            if (value.length > 2) {
                this._name = value;
            }
            console.log("Rejected")
        }
    }

    let person = new Pserson('Max');
    console.log(person._name); //it's not really private but can project more.
    person.name = 'Anna';
    console.log(person._name);
```

    6. Extending Built-in Object
       "Subclassing": [https://kangax.github.io/compat-table/es6/]

```javascript
    class ConvertableArray extends Array {
        convert() {å
            let returnArray = [];
            this.forEach(value => returnArray.push('Converted!' + value));
            return returnArray;
        }
    }
    let numberArray = new ConvertableArray();
    numberArray.push(1);
    numberArray.push(2);
    numberArray.push(3);

    console.log(numberArray.convert());
    //print ["Converted!1", "Converted!2", "Converted!3"] we can

```

#### 1.1.2. Symbols

Symbols are part of **meta-programming** programming tools introduced by ES6. Its a new primitive type. It's unique identifier.

    1. Symbol basic

```javascript
    let symbol = Symbol('debug'); //Symbol Class don't need use 'new' keyword to define a new object.
    let anotherSymbol = Symbol('debug');
    console.log(typeof symbol); //'symbol'
    console.log(symbol === anotherSymbol) //they stand for different unique ID.

    let obj = {
        name: 'max',
        [symbol]: 22
    }

    console.log(obj); // It doesn't pront symbol.
    console.log(obj[symbol]); //22 <- you can use it when u need to meta-programming.

```

    2. Shared symbols

```javascript
    let symbol1 = Symbol.for('age');
    let symbol2 = Symbol.for('age');

    let person = {
        name: 'Max',
        age: 30
    };

    function makeAge(person) {
        let ageSymbol =Symbol.for('age');
        //if let ageSymbol = Symbol('age'); -> It will be different.
        person[ageSymbol] = 27;
    }

    makeAge(person);
    console.log(person[symbol1]);   //27
    console.log(person[symbol2]);   //27
    console.log(person["age"]);     //30 <- It's not override the properties in class.

```

    2. Well-known symbols
    There are well known symbols already implemented in Javascript like below.

```javascript
    class Person {

    }
    Person.prototype[Sypmbol.toStringTag] = 'Person'
    let person = new Person();
    console.log(person);    //[object Object] {... } -> [object Person]
```

    One more example on MDN page.

```javascript

    let numbers = [1,2,3];
    console.log(numbers + 1);   //"1,2,31"
    numbers[Symbol.toPrimitive] = function () {
        return 999
    }
    console.log(numbers + 1);   //1000
```

## 2. Node JS

* * *

