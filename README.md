# Conditional Rendering in React

<img src="https://meetinmontauk.com/wp-content/uploads/2015/04/lebowski_condition.jpg"/>


React is an incredible framework with tremendous power. One of the most powerful parts of working with React is the ability to run conditions on what we render on our screen.

There are a few ways to condtionally render our data
- Ternaries vs If / Else Statements vs Switch Statements
- Rendering Components vs Rendering Data
- Switch Statements returning Components

All of these methods are acceptable to use and will have their own use cases. The most important thing to remember is that the Return Statement goes inside of our If/Else Statements, while Ternaries go into our Return Statements.


Of course, with Props in React, we are able to pass data between multiple components, allowing our pages to appear totally different based on the conditions we're in!

Now, lets see what condition our condition is in


## Ternaries vs If/Else


### If Else Statements

We'll start with our If Else statement. Remember, we need to import our 2 components into our Layout.jsx first, and make sure we have our props pulled from the parent component:


```jsx
//Layout.jsx

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
//Layout.jsx

const Layout =(props) => {
 return {
    if (!props.isLoggedIn) {
      return <IsLoggedOut />
 }
  else {
     return <IsLoggedIn />
}

```

<img src ="https://static1.srcdn.com/wordpress/wp-content/uploads/2020/11/Jeff-Bridges-in-The-Big-Lebowski.jpg"/>

As you can see, we can render whole components into our conditions, how cool is that!


But wait! We know that we want to have our user's name displayed on screen, let's add some props in. We do this the same way we've been working on, like this!

```jsx

return <IsLoggedIn userName = {props.userName}/>

```


### Ternaries

Ternaries in React work the same way they do in regular Javascript operations. And like our If Else's, we can return either full components, or regular data within. Lets go into our Header file, make sure we're pulling in props, and return some information based on whether or not we are logged in:

```jsx
//Header.jsx

const Header = (props) => {
    console.log(props)
    const isLoggedIn = props.isLoggedIn
    
    return isLoggedIn ?  <h2>Welcome! </h2> : <h2> Create Account</h2>
}

export default Header
```

<img src ="https://is1-ssl.mzstatic.com/image/thumb/VQxilvxrSKyrw4KaQkeyYQ/1200x675mf.jpg"/>

Ternaries can be a bit confusing at first, but they all follow this similar syntax. Try them out, and see how much better you feel with them after a few attempts!

### Switch Statements:

Switch Statements are yet another way of setting a condition to render our data. They follow the same rules as they did in vanilla javascript. It would look something like this if we were to use them in our code:

```jsx

const userType = "guest"

switch (userType) {
      case "guest":
        return <GuestComponent/>
        break

      case "user":
        return <UserComponent/>
        break

      case "admin:
        return <AdminComponent/>
        break

      default:
        return <IsLoggedOut/>

}
```

### Guard Operators

<img src ="https://static1.cbrimages.com/wordpress/wp-content/uploads/2022/01/Walter-Dismisses-The-Dude-In-The-Big-Lebowski.jpg"/>

Conditional Rendering in React is wonderful for things like Logged In/Out variables, but it also has an incredibly powerful usage when pulling API data. Because it may take a few ms longer to pull and render the data than for the React DOM to load, it is very common to see errors saying our data is null/undefined when working with live data. We can use conditional rendering to prevent this by adding in a placeholder until the data loads up.

This follows the same rules, and can be written in many forms. It is common to use our && operators so that we are sure we are getting all of our data before we load up. This Two of the ways we will see may look like this:

If Else Statements:
```jsx

if (response.data && response.data.userName) {
return {
 <h1> Welcome {response.data.userName} </h1>
 }
} else {
return {
 <h2> Loading Please Wait </h2>
  }
}
```

And for individual peices of data, like the "Prime Eligiable" or "On Sale!" blocks in amazon


```jsx

return {
 response.data.isPrimeEligable ? <h2> 20% Off Sale Now! </h2> : null
}

```

These can add a massive amount of control and power to our sites, especially when working with large data sets, like we'll see later this week!

So relax, using these few peices of code, we should be able to prevent any errors, and keep our pages loading up smooth!


<img src ="https://static1.srcdn.com/wordpress/wp-content/uploads/2023/02/the_dude_listening_to_a_tape_in_the_big_lebowski.jpg" />
