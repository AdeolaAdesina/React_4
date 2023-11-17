# React Component and advanced JSX

## Use Multiline JSX in a Component

In this lesson, you will learn some common ways that JSX and React components work together. You’ll get more comfortable with both JSX and React components while picking up some new tricks.

Take a look at this HTML:

```
<blockquote>
  <p>
    The world is full of objects, more or less interesting; I do not wish to add any more.
  </p>
  <cite>
    <a target="_blank"
      href="https://en.wikipedia.org/wiki/Douglas_Huebler">
      Douglas Huebler
    </a>
  </cite>
</blockquote>
```

How might you make a React component return this HTML?

Select QuoteMaker.js to see one way of doing it.

The key thing to notice in QuoteMaker is the parentheses in the return statement, on lines 4 and 16. Until now, your function component return statements have looked like this, without any parentheses:

```
return <h1>Hello world</h1>;
```

However, a multi-line JSX expression should always be wrapped in parentheses! That is why QuoteMaker‘s return statement has parentheses around it.

![Screenshot 2023-11-17 at 05 16 21](https://github.com/AdeolaAdesina/React_4/assets/29931071/0e12a367-e976-4fd5-bbb6-b3e8ec961f66)


E.g


```
import React from 'react';

const redPanda = {
  src: 'https://upload.wikimedia.org/wikipedia/commons/b/b2/Endangered_Red_Panda.jpg',
  alt: 'Red Panda',
  width:  '200px'
};

function RedPanda(){
    return (
      <div>
        <h1>Cute Red Panda</h1>
        <img 
          src={redPanda.src}
          alt={redPanda.alt}
          width={redPanda.width} />
      </div>
    );
}

export default RedPanda;
```


![Screenshot 2023-11-17 at 05 23 40](https://github.com/AdeolaAdesina/React_4/assets/29931071/5332c186-cf7b-4511-957a-6b67e65a2932)




## Putting Logic in a Function Component

A function component must have a return statement. However, that isn’t all that it can have.

You can also put simple calculations that need to happen before returning your JSX element within the function component.

Here’s an example of some calculations that can be done inside a function component:

```
function RandomNumber() {
  //First, some logic that must happen before returning
  const n = Math.floor(Math.random() * 10 + 1);
  //Next, a return statement using that logic: 
  return <h1>{n}</h1>
}
```

Watch out for this common mistake:

```
function RandomNumber() {
  return (
    const n = Math.floor(Math.random() * 10 + 1);
    <h1>{n}</h1>
  )
}
```


In the above example, the line with the const n declaration will cause a syntax error, as it should come before the return.

Example:


```
import React from 'react';

const friends = [
  {
    title: "Yummmmmmm",
    src: "https://content.codecademy.com/courses/React/react_photo-monkeyweirdo.jpg"
  },
  {
    title: "Hey Guys! Wait Up!",
    src: "https://content.codecademy.com/courses/React/react_photo-earnestfrog.jpg"
  },
  {
    title: "Yikes",
    src: "https://content.codecademy.com/courses/React/react_photo-alpaca.jpg"
  }
];

// New function component starts here:
function Friend() {
  const friend = friends[0];

  return (
    <div> 
      <h1>
        {friend.title}
      </h1>
      <img 
        src={friend.src}
      />
    </div>
  );
}

export default Friend;
```


![Screenshot 2023-11-17 at 05 31 58](https://github.com/AdeolaAdesina/React_4/assets/29931071/72c48ae1-3217-42db-b9d0-64ad90870892)



## Use a Conditional in a Function Component

How might you use a conditional statement inside of a function component?

Select TodaysPlan.js to see one way of doing it.

Notice that the if statement is located inside of the function component, but before the return statement.



```
import React from 'react';

const fiftyFifty = Math.random() < 0.5;

// New function component starts here:
function TonightsPlan() {
    if (fiftyFifty) {
      return <h1>Tonight I'm going out WOOO</h1>;
    } else {
      return <h1>Tonight I'm going to bed WOOO</h1>;
    }
}
export default TonightsPlan;
```

![Screenshot 2023-11-17 at 05 37 39](https://github.com/AdeolaAdesina/React_4/assets/29931071/8abff064-add7-496c-81f5-649862292c03)


## Event Listener and Event Handlers in a Component

Your function components can include event handlers. With event handlers, we can run some code in response to interactions with the interface, such as clicking.

```
function MyComponent(){
  function handleHover() {
    alert('Stop it.  Stop hovering.');
  }
  return <div onHover={handleHover}></div>;
}
```

In the above example, the event handler is handleHover(). It is passed as a prop to the JSX element ```<div>```. We’ll discuss more on props in a later lesson, but for now, understand that props are information passed to a JSX tag.


The logic for what should happen when the ```<div>``` is hovered on is contained inside the handleHover() function. The function is then passed to the ```<div>``` element.

Event handler functions are defined inside the function component and, by convention, start with the word “handle” followed by the type of event it is handling.

There’s a small quirk you should watch out for. Take a look at this line again:

```
return <div onHover={handleHover}></div>
```

The handleHover() function is passed without the parentheses we would typically see when calling a function. This is because passing it as handleHover indicates it should only be called once the event has happened. Passing it as handleHover() would trigger the function immediately, so be careful!


E.g

```
import React from 'react';

function SubmitButton() {
  function handleClick() {
    alert('Submission Successful.');
  }
  return <button onClick={handleClick}>Submit</button>;
}

export default SubmitButton;
```


![Screenshot 2023-11-17 at 05 42 18](https://github.com/AdeolaAdesina/React_4/assets/29931071/3838c955-2adf-4f2b-b437-6f3ba0a17cc2)




