# Conditional Rendering in React

React is an incredible framework with tremendous power. One of the most powerful parts of working with React is the ability to run conditions on what we render on our screen.

There are a few ways to condtionally render our data
- Ternaries vs If / Else Statements vs Switch Statements
- Rendering Components vs Rendering Data

All of these methods are acceptable to use and will have their own use cases.

Of course, with Props in React, we are able to pass data between multiple components, allowing our pages to appear totally different based on the conditions we're in!


## Ternaries vs If/Else


### If Else Statements

We'll start with our If Else statement. Remember, we need to import our 2 components into our Layout.jsx first, and make sure we have our props pulled from the parent component:


```jsx
Layout.jsx

import IsLoggedIn from './IsLoggedIn'
import IsLoggedOut from './IsLoggedOut'


const Layout =(props) => {
 return {
    //code goes here!
 }
}

```


Once we have our imports, we can run our code.  The main rule to follow is that Ternaries are run *inside* of a return statement, while the return is kept *inside* of our If Else's. 

Our Layout should like this. There are a few ways of doing this, for this lesson, we are going to set our conditional to start with a falsey statement, using the Bang Opertor. What this is saying is that if ifLoggedOut is falsey, we'll return the component for that, Else we'll return the Logged In component


```jsx
const Layout =(props) => {
 return {
    if (!props.isLoggedIn) {
      return <IsLoggedOut />
 }
  else {
     return <IsLoggedIn />
}

```

As you can see, we can render whole components into our conditions, how cool is that!


But wait! We know that we want to have our user's name displayed on screen, let's add some props in. We do this the same way we've been working on, like this!

```jsx

return <IsLoggedIn userName = {props.userName}/>

```


### Ternaries


