# Learn-React
### 2020-01-23 11:57:58
~~~
import React from 'react';
import ReactDOM from 'react-dom';

class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}

// component goes here:
ReactDOM.render(
  <MyComponentClass/>,
  document.getElementById('app')
  )
~~~
A render method must contain a return statement. Usually, this return statement returns a JSX expression:

~~~
class ComponentFactory extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}
~~~

A render method is a property whose name is render, and whose value is a function. The term “render method” can refer to the entire property, or to just the function part.

~~~
class ComponentFactory extends React.Component {
  render() {}
}
~~~

Component class variable names must begin with capital letters eg **MyComponentClass**!

~~~
import React from "react"
import ReactDOM from 'react-dom'

class MyComponentClass extends React.Component {
  
}
~~~

### 2020-01-17 10:20:31
#### THE COMPONENT
~~~
import React from 'react';
import ReactDOM from 'react-dom';

class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
};

ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
);

~~~
#### React.createElement
You can write React code without using JSX at all!

The majority of React programmers do use JSX, and we will use it for the remainder of this tutorial, but you should understand that it is possible to write React code without it.

The following JSX expression:
~~~
const h1 = <h1>Hello world</h1>;
can be rewritten without JSX, like this:

const h1 = React.createElement(
  "h1",
  null,
  "Hello, world"
);
~~~

#### Keys
**keys** don’t do anything that you can see! React uses them internally to keep track of lists. If you don’t use keys when you’re supposed to, React might accidentally scramble your list-items into the wrong order.

~~~
import React from 'react';
import ReactDOM from 'react-dom';

const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map((person, i) =>
  // expression goes here:
  <li key={'person_' + i}>{person}</li>
);

// ReactDOM.render goes here:
ReactDOM.render(<ul>{peopleLis}</ul>, document.getElementById('app'));
~~~

#### .map in JSX
~~~
import React from 'react';
import ReactDOM from 'react-dom';

const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map(person =>
  // expression goes here:
  <li>{person}</li>
);

// ReactDOM.render goes here:
ReactDOM.render(<ul>{peopleLis}</ul>, document.getElementById('app'));
~~~

### 2020-01-16 12:26:24
#### JSX Conditionals: &&
Below code the const judmental when false Nacho cheez will appear
~~~
import React from 'react';
import ReactDOM from 'react-dom';

// judgmental will be true half the time.
const judgmental = Math.random() < 0.5;

const favoriteFoods = (
  <div>
    <h1>My Favorite Foods</h1>
    <h1>judgmental is {judgmental === true ? 'true' : 'false'}</h1>
    <ul>
      <li>Sushi Burrito</li>
      <li>Rhubarb Pie</li>
      {!judgmental && <li>Nacho Cheez Straight Out The Jar</li>}
      <li>Broiled Grapefruit</li>
    </ul>
  </div>
);

ReactDOM.render(
	favoriteFoods, 
	document.getElementById('app')
);

~~~

Every time that you see && in below example, either some code will run, or else no code will run.

**&&** works best in conditionals that will sometimes do an action, but other times do nothing at all.

~~~
const tasty = (
  <ul>
    <li>Applesauce</li>
    { !baby && <li>Pizza</li> }
    { age > 15 && <li>Brussels Sprouts</li> }
    { age > 20 && <li>Oysters</li> }
    { age > 25 && <li>Grappa</li> }
  </ul>
);
~~~

#### JSX Conditionals: The Ternary Operator
~~~
import React from 'react';
import ReactDOM from 'react-dom';

function coinToss () {
  // Randomly return either 'heads' or 'tails'.
  return Math.random() < 0.5 ? 'heads' : 'tails';
}

const pics = {
  kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
  doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
};

const img = <img src={pics[coinToss() === 'heads' ? 'kitty' : 'doggy']} />;

ReactDOM.render(
	img, 
	document.getElementById('app')
);
~~~
~~~
const headline = (
  <h1>
    { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
  </h1>
);
~~~

#### JSX Conditionals: If Statements That Don't Work

~~~
import React from 'react';
import ReactDOM from 'react-dom';

function coinToss() {
  // This function will randomly return either 'heads' or 'tails'.
  return Math.random() < 0.5 ? 'heads' : 'tails';
}

const pics = {
  kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
  doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
};
let img;

// if/else statement begins here:
if (coinToss() === "heads")
 {
  img = (
    <img src={pics.kitty} />
    )
} else {
 img = (
    <img src={pics.doggy} />
    )
}

ReactDOM.render(img, document.getElementById('app'));
~~~

#### Event Listeners in JSX

Note that in HTML, event listener names are written in all lowercase, such as onclick or onmouseover. In JSX, event listener names are written in camelCase, such as onClick or onMouseOver.

An event listener attribute’s value should be a function. 


~~~
import React from 'react';
import ReactDOM from 'react-dom';

function makeDoggy(e) {
  // Call this extremely useful function on an <img>.
  // The <img> will become a picture of a doggy.
  e.target.setAttribute('src', 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg');
  e.target.setAttribute('alt', 'doggy');
}

const kitty = (
	<img 
		src="https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg" 
		alt="kitty"
    onClick={makeDoggy}/>
);

ReactDOM.render(kitty, document.getElementById('app'));
~~~

### 2020-01-15 15:39:06

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