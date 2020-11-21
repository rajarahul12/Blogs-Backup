## What is React.js and Why is React.js created? 🤔

React.js is one of the most popular JavaScript libraries but before going right into it let's take a step back and understand how websites were developed a few years back.

Long back websites were built mostly with HTML, CSS, and very little JavaScript. As more and more businesses and people started using websites; the interactions increased on a website. Whenever there is a change that needs to be done to the *DOM* that required reloading of the entire page.

### What is DOM?

> *Document Object Model* is a tree-like structure that browsers understand that is how they render the web page. Whatever we write into an HTML file, browsers create a DOM out of it and renders it.

*Example of how a DOM might look like:*

![Screenshot 2020-11-22 at 1.06.08 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605988231114/CsZ8Z_59T.png)

So in order to handle complex interactions developers needed an easier way to change and modify the HTML content/DOM of the page. That is when **jQuery** came in and it was adopted quite heavily by the developers and it does the job of DOM Manipulation quite well for some time.

But websites started becoming large, and it became complicated to handle a lot of user interactions, and due to jquery websites started feeling a little slow. That is when the *Single Page Applications* became popular with the intervention of Angular. 

### What are Single Page Applications?


> A single page application is nothing but a website with a single HTML page and multiple JS files and all of them are downloaded at once so there is no need of downloading different pages based on user interactions. All the updates to HTML and content are done on the client-side using JavaScript

After a few years of Angular's domination, Facebook came up with *React.js* which they internally used for building Facebook and then open-sourced after seeing its success and its ability to handle millions of users daily on its website.

### What is React.js?


> React.js is a javascript library for building User Interfaces. What react does beautifully is reacting to the changes and user interactions.

The rule that React follows is whatever update needs to be done to the page/HTML you don't directly do it. You tell me what needs to be updated and I will do it efficiently without actually reloading the website. React uses something called virtual DOM to achieve this. 

### What is Virtual DOM?

*Let's take an Example*

If your laptop screen is broken would you change your entire laptop or just the screen?
Just the screen right, wouldn't it be nice if we had something like this for the websites where you make changes to a part of the DOM, only that part gets modified and rendered again instead of the whole DOM.

React creates a tree of custom objects each representing the part of a DOM. If we create an h1 tag react internally will create `React.h1` object, similarly for other tags as well and it can modify these objects very quickly rather than modifying and traversing the real DOM. Before a component(we will be discussing what are components very soon) is loaded, it will determine what needs to be changed using the virtual DOM and intelligently syncs/updates it in the actual DOM.


> To summarize Virtual DOM is a blueprint of the actual DOM and whatever needs to be updated, React updates it in the virtual DOM and intelligently syncs/updates it in the actual DOM without the need to reload the page.

Now that we understood how React is powerful. Let's also look at some of the concepts you need to understand in React


### Component: 

> A component is nothing but part of the page that can be reused. A website created using React is made up of multiple components. 

In the below image, you can see the Post Component, you can build it once and it can be reused as many times as needed. Along with Post, there are other components as well, so you get to *isolate code based on their functionality*.


![Screenshot_2020-11-21_at_10_58_36_PM-2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1605988264937/G584MTPjF.png)

We have been talking a lot, Let's take a look at some code - Finally :)

This is how a typical component looks like

```
// Header.js
// This is functional component
import React from 'react'

function Header() {
  return (
    <div>
      <h1>Hello, there</h1>
      <p>Welcome to React Blog</p>
    </div>
  )
}

export default Header
``` 


```
// Header.js
// This is a class component
export default class Header extends Component {
  render() {
    return (
      <div>
        <h1>Hello, there</h1>
        <p>Welcome to React Blog</p>
      </div>
    )
  }
}
``` 


> Think of a component this way - A component is a JavaScript function or a class that returns a piece of code that looks like HTML (but it is actually JSX) that can be used whenever needed.

### What is JSX?
JSX stands for JavaScript XML. JSX allows us to write HTML in React

In this way, you can write multiple components, and the way you render these components is just by using them as HTML tags 
```
// Rendering the Header component
<Header />
``` 

The other two important terminologies that you need to understand are State and Props.

### STATE: 

> A state is a javascript Object that holds some information about the component that may change over the lifetime of the component. 

Remember when we talked about Virtual DOM we said that react intelligently updates the DOM itself we just need to tell react what are the things that need to be changed. That is possible with State. So if you want to change something on a page use state there.

*Let's take an example:*

You have user input and you want react to take care of updating it whenever the user enters something. That is when you use a state.


```
export default class Header extends Component {

  // Initialize state
  state = {
    name: "there"
  }

  render() {
    return (
      <div>
        <h1>Hello, {this.state.name}</h1>
        <p>Welcome to React Blog</p>
        <input type="text" onChange={(e) => this.setState({name: e.target.value})} />
      </div>
    )
  }
}
``` 

Let's break it down
1. We initialized a piece of state called name and gave an initial value to it
2. We can access the state using `this.state.name`
3. We have an `onChange` event for the input. Here whenever there is a change to the input we are updating the state variable using `this.setState` to whatever user entered. Remember we are only updating the state and react will take care of updating it wherever needed in the DOM. In this case, it is the h1 tag. If the user enters John it will show *Hello, John*.

**NOTE**: Never update a state variable like a normal variable i.e., `this.state.name="John Doe"`. React will not know to update the DOM if we update the state manually. With `setState` react knows what has changed and what to update, using `setState` we tell react that changes in the DOM are needed.


### PROPS:

> Props are nothing but arguments that are sent to a component. The value of a prop cannot be changed in the entire component.

Remember we talked about the Components and saw an example of a Post Component. If you clearly observe we said we can re-use the component but the way you can re-use is by changing the props. That is how even the component is the same you are able to see different content in both the posts.

Now how do you pass these `props` to a component?  🤔


Props are passed to a component while we render the component.

```
<Header name="John" />
``` 
And you can access the props this way

```
{this.props.name}
``` 

Complete component

```
export default class Header extends Component {
  render() {
    return (
      <div>
        <h1>Hello, {this.props.name}</h1>
        <p>Welcome to React Blog</p>
      </div>
    )
  }
}
``` 


This covers the basics you need to understand React but there is still a lot more to discuss like

- Component LifeCycle Methods

- State Management

- React hooks

and much much more. So I will cover these topics in the upcoming articles. Until then have a good day.

Let me know in the comments what other topics you want me to cover. I will try to cover those in my next article.


