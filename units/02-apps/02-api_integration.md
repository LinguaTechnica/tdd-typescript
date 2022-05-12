# Part 3: Integration

You should have completed Parts 1 and 2 before proceeding to this section.

## Tools 

For this phase, you'll have some tools you can rely on to make development a bit easier:

* Webpack 

Webpack will provide a development server which can automatically compile and recompile your code as you work. That will take some of the tedium out of the process. 


## API Integration 

Now that you have a UI and an app, it's time to tie these things together by binding data to the DOM. The data comes from your app and the DOM is represented by the UI. 

For this section, you won't need to write any tests. Your task is to:

1. Use Typescript to make the UI interactive.
2. Compile your TS to JS and import it into your HTML file. 
3. Use this item data: [Vending Machine Snacks @ Github Gist](https://gist.github.com/Protosac/ac091a6734589468335146b6fefde6e2)

## Compilation 

Compilation is what transforms your Typescript to Javascript. Browsers only understand ECMAScript (JS). 

We've been using tools that make on-the-fly compilation simple and easy as we write tests and code with TS. For this part, you'll have to do it on your own -- for now. 

For this, you can use the compiler that comes with Typescript using the `tsc` command. Below are some examples you can try on your own. 

```bash
# display all available command options
tsc -h

# compile a specific file
tsc myfile.ts 

# compile a folder of files
tsc --build tsconfig.json 
```

### Compiling Multiple Files 

To compile multiple files at once you must define a `tsconfig.json`. For this exercise, it has been defined for you. Please take the time to look it over and [understand the options](https://www.typescriptlang.org/tsconfig). 

```json 
{
  "compilerOptions": {
    "noEmit": false,
    "allowJs": true,
    "target": "ES6",
    "module": "ES6", 
    "moduleResolution": "Node",
    "strict": true,
    "sourceMap": true,
    "outDir": "public/scripts",
    "skipLibCheck": true
  },
  "exclude": ["node_modules", "**/*.test.ts"],
  "files": [
    "src/index.ts"
  ]
}
```

### !callout-warn 
### Node and ES6 
ES2015 and ES6 are the same thing, but you'll see both used out in the wild, in addition to other JS versions. 

Node is of course JS, but relies on its own modules in addition to standard JS modules. This distinction is important because it means that code you write in your editor using Node may behave differently if you try to use it directly in the browser. Specifically, `require`, `import` and `export` statements are Node commands and your browser will not understand them. 
### !end-callout

Many options are fairly self explanatory or at least familiar. For example `strict` is very similar to the `use strict;` declaration used in JS. Another straightforward option is `outDir`, which names the path to a directory where files will be output during compilation. 

Some less obvious options of note:

- `noEmit`: determines whether new files will be generated or not. 
- `sourceMap`: map files help your app find the original source code from your minified JS.
- `files`: An array of files you want the compiler to compile.

Source maps in particular are important to understand, so be sure to take a look at the [MDN guide](https://developer.mozilla.org/en-US/docs/Tools/Debugger/How_to/Use_a_source_map).

To keep things simple, our file is configured to only compile 1 file: `src/index.ts`. This is a common practice: it allows you to write your integration script in 1 file while importing all the others that you need to use. Imported files are automatically compiled with it. For example, if `VendingMachine.ts` was imported in the `index.ts` file, compiling the latter will also compile the former, since it's required for the module to work.

Feel free to add and edit the `tsconfig.json` to see how the different options work. But be sure you're commiting your code frequently in case you break something!

## Manipulating the DOM with JS 

Javascript is made for manipulating the DOM and provides some handy objects to make it very easy. Below are the most basic and common objects you'll use: 

**Finding Elements**
```ts 
const div = document.getElementById('myDivName');
const buttons = document.getElementsByClass('moneyOption');

const machineDiv = document.querySelector('#vendingMachine');
const itemElements = document.querySelectorAll('#item');

const paragraphs = document.getElementsByTagName('p');
```

**Creating Elements**
```ts 
let snackDiv = document.createElement('div');
```

**Element Properties**
```ts 
const div = document.getElementById('snackList');
const element = document.getElementById('snack');

element.innerHTML = '<h1>Snack Name</h1>';
element.setAttribute('class', 'snacks');

div.innerText = 'Snack List';
div.appendChild(element);
```

**Events**

Events help add interactivity to your UI. There are 2 ways to add events. The first is in the HTML:

```html 
<button onclick="myFunc()" id="clickMe">Click Me!</button>
```

Or in your app: 
```ts 
const button = document.getElementById('clickMe');
button.addEventListener('click', myFunc);

function myFunc(event: Event) {
    alert('Button clicked'!);
}
```

In this example, `addEventListener` passes an `Event` object to the `myFunc` callback. That event will contain all data related to the event. For example: 

```ts 
function updateDepositDisplay(event: any): void {
    let money = event.target.innerText;

    vendingMachine.insert(parseInt(money));
    console.log('Deposited: ', money);
}
```

The event in this case has text data in the HTML element that we want to retrieve.

### !callout-info
Remember: **Everthing** in the DOM is a string. Even the numbers!
### !end-callout

