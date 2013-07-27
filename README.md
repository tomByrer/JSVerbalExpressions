VerbalExpressions v0.1
=====================

## JavaScript Regular Expressions made easy
VerbalExpressions is a JavaScript library that helps to construct difficult regular expressions.

## Other Implementations
You can see an up to date list of all ports in our [organization](https://github.com/VerbalExpressions).
- [Ruby](https://github.com/VerbalExpressions/RubyVerbalExpressions)
- [C#](https://github.com/VerbalExpressions/CSharpVerbalExpressions)
- [Python](https://github.com/VerbalExpressions/PythonVerbalExpressions)
- [Java](https://github.com/VerbalExpressions/JavaVerbalExpressions)
- [PHP](https://github.com/VerbalExpressions/PHPVerbalExpressions)

## How to get started
### In the browser
```HTML
<script type="text/javascript" src="VerbalExpressions.js"></script>
```
### On the server (node.js)
Install:
```
npm install verbal-expressions
```
Require:
```javascript
var VerEx = require("verbal-expressions");
```

## Examples

Here's a couple of simple examples to give an idea of how VerbalExpressions works:

### Testing if we have a valid URL

```javascript
// Create an example of how to test for correctly formed URLs
var tester = VerEx()
            .startOfLine()
            .then( "http" )
            .maybe( "s" )
            .then( "://" )
            .maybe( "www." )
            .anythingBut( " " )
            .endOfLine();

// Create an example URL
var testMe = "https://www.google.com";

// Use RegExp object's native test() function
if( tester.test( testMe ) ) alert( "We have a correct URL "); // This output will fire
else alert( "The URL is incorrect" );

console.log( tester ); // Ouputs the actual expression used: /^(http)(s)?(\:\/\/)(www\.)?([^\ ]*)$/ 
```

### Replacing strings

```javascript
// Create a test string
var replaceMe = "Replace bird with a duck";

// Create an expression that seeks for word "bird"
var expression = VerEx().find( "bird" );

// Execute the expression like a normal RegExp object
var result = replaceMe.replace( expression, "duck" );

alert( result ); // Outputs "Replace duck with a duck"
```

### Shorthand for string replace:

```javascript
var result = VerEx().find( "red" ).replace( "We have a red house", "blue" );
alert( result ); // Outputs "We have a blue house"
```

## API documentation

You can find the API documentation at the [wiki pages](https://github.com/jehna/VerbalExpressions/wiki).

## A little word for a big help
I'd like to promote a special thank-you to [Ben Nadel][ben-nadel] for his [great article about extending native JS objects][extending]

## Contributions
Clone the repo and fork:
`git clone https://github.com/jehna/VerbalExpressions.git`.

Pull requests are warmly welcome!

[ben-nadel]:http://www.bennadel.com/
[extending]:http://www.bennadel.com/blog/2292-Extending-JavaScript-Arrays-While-Keeping-Native-Bracket-Notation-Functionality.htm
