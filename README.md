# Learn-React

### 2020-01-15 15:39:06
#### Event Listeners in JSX


----
When writing JSX, it’s common to use variables to set attributes.

~~~
import React from 'react';
import ReactDOM from 'react-dom';

const goose = 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-goose.jpg';

// Declare new variable here:

const gooseImg = (
  <img src={goose} />
);

ReactDOM.render(gooseImg, document.getElementById('app')); 
~~~

---
When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.


~~~
import React from 'react';
import ReactDOM from 'react-dom';

const theBestString = 'tralalalala i am da best';

ReactDOM.render(<h1>{theBestString}</h1>, document.getElementById('app'));
~~~

---
You can render actual javascript inbetween curly braces. For example `{2 + 3}` is simple Javascript.
~~~
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
ReactDOM.render(
  <h1>{2 + 3}</h1>,
  document.getElementById('app')
);

~~~
---

Need to use a closing forward slash in JSX

~~~
Fine in JSX:

  <br />

NOT FINE AT ALL in JSX:

  <br>

~~~

---
In HTML, it’s common to use class as an attribute name:

`<h1 class="big">Hey</h1>`

In JSX, you can’t use the word class! You have to use className instead:

`<h1 className="big">Hey</h1>`

---

One special thing about ReactDOM.render() is that it only updates DOM elements that have changed.

That means that if you render the exact same thing twice in a row, the second render will do nothing:

~~~
const hello = <h1>Hello world</h1>;

// This will add "Hello world" to the screen:

ReactDOM.render(hello, document.getElementById('app'));

// This won't do anything at all:

ReactDOM.render(hello, document.getElementById('app'));

~~~

---
**ReactDOM.render()**'s first argument should evaluate to a JSX expression, it doesn’t have to literally be a JSX expression.

The first argument could also be a variable, so long as that variable evaluates to a JSX expression.

~~~
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
const myList = (
  <ul>
    <li>Learn React</li>
    <li>Become a Developer</li>
  </ul>
);
ReactDOM.render(myList, document.getElementById('app'));
~~~
---
The following code will render a JSX expression:

**document.getElementById('app')** is the second argument which tells where to insert the JSX. This could be `<main id="app"></main>` in the html file.

~~~
ReactDOM.render(<h1>Hello world</h1>,
document.getElementById('app'));
~~~
---
JSX Outer Elements need to have exactly one container so below wont work:
~~~
const paragraphs = (
  <p>I am a paragraph.</p> 
  <p>I, too, am a paragraph.</p>
);
~~~
---
multi-line JSX expression in parentheses
~~~
const myDiv = (
  <div>
    <h1>Hello World</h1>
  </div>
);
~~~