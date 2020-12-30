## React vs Angular: Which one to choose for your Web App?

In this blog, we'll talk about two heavily used JavaScript frameworks/libraries for developing websites.

React vs Angular - which one to choose for developing Websites?

## 🔎 Brief Overview: What is React, Angular?
Before we go any further, let's see what both React and Angular are actually are

### What is React?

ReactJS is a JavaScript library developed internally by Facebook for this Facebook ADs app and later made public in May 2013. React uses a declarative style(You don't directly change individual parts of the app in response to various user events instead React will take care of updating the DOM you just need to tell it what the app should look like) programming to describe the UI state.

React can also be used to build Hybrid Mobile applications, Native Mobile applications, Desktop applications.

### What is Angular?

Let's get the confusion out of the equation between Angular and Angular JS

The latest versions are called Angular 2 (Angular 2, 4, 5, 6, 7, 8, 9, 10, 11) whereas Angular JS is a completely different and old framework that got a complete re-write and that is called Angular / Angular 2

Angular is a full-fledged JavaScript framework that has everything developers need to build large-scale apps

-> Both React and Angular are open-source projects that means anyone can contribute to the source code.

## 🌐  Language Support

-> **React** uses JavaScript ES6+ and JSX(JavaScript XML that is quite similar to HTML, it allows us to write HTML inside JavaScript)

-> **Angular** uses JavaScript and TypeScript(It is a strict syntactical superset of JavaScript and adds optional static typing to JavaScript)

## 🧱 App Structure

### React

React approaches building UI by breaking them into smaller pieces called Components. These components are re-usable. Each component will manage its own state and these components can be combined to build complex UI's

But since React is just a UI library it requires some other tools to render the webpage in a browser.

- **Webpack**: A module bundler to combine multiple JavaScript and CSS files for each component into one

- **Babel**: A transpiler that converts JSX and ES6+ JavaScript into a version that all browser can understand and support

### Angular

Angular approaches building UI using the complex Model, View, Controller architecture.
Since Angular is a full-fledged package you don't need any additional configuration ad it comes with it out of the box.

-> Both React and Angular are robust technologies but React offers more flexibility and options to choose different things Router, State Management Libraries yourself.

## 💯 DOM and Performance

**React** uses Virtual DOM(Virtual DOM is a blueprint of the actual DOM) and whatever needs to be updated, React updates it in the virtual DOM and intelligently syncs/updates it in the actual DOM without rewriting the entire HTML doc virtually. This renders updates much faster and ensures fast performance – no matter the apps' size

**Angular** operates on Real DOM, this results in re-rendering the entire HTML tree structure. The real DOM feature makes it's apps slower when dealing with a lot of data requests.

## 📊 Data Binding 

Data binding is about synchronizing data between business logic and UI.

**React** uses one-way data binding whereas **Angular** uses both one-way and two-way data binding

One-way binding makes the code more stable, and also makes debugging an app build with React much easier compared to an Angular app. But, both one-way and two-way binding of Angular is simpler to work with and makes the framework more flexible.


## 🔙 Backward Compatibility

An application needs to be regularly updated.

The difference between React and Angular is that React has full backward compatibility. Being a library in itself, it’s easier for React to update its previous releases with new ones.

As for Angular, it’s impossible to jump from Angular 2.0 to 11.0. First, you need to install updates between the versions, one by one. If you plan to step-by-step enhance the project by adding new features, React might be the best choice since it has absolute backward compatibility.

## 📏 Bundle Size

The smaller the size of the app the faster it takes to load the web page.

React is **~97.5KB** in size(*minified*) and Angular is **~766KB** in size(*minified*) which is very big compared to React. But still, it not safe to say that React is faster. As you add a lot of external libraries when it comes to React so it is seen that React+Redux has a bigger app size compared to Angular.

Complete Comparison  can be found  [here](https://www.altexsoft.com/blog/engineering/react-vs-angular-compared-which-one-suits-your-project-better/#:~:text=Also%2C%20Angular%20has%20a%20smaller,React%20%2B%20Redux%20is%20193%20KB.&text=The%20recent%20updates%20to%20Angular,of%20speed%20or%20app%20size.) 

**Angular** solves its larger size problem by not including the entire bundle of Angular framework in the user's app. As part of the build process, it gets rid of:

- Development utilities
- Unused modules

Then, minification and compression take place allowing the framework to perform extra optimizations.

**React** uses WebPack, and web pack does a few optimizations like

- Tree Shaking
- Minification
- Dynamic Imports reduce the bundle size

## ⚖️ Scalability

React relies heavily on third-party tools so it might become a problem later in the future when you want to scale. But architecting your app in a better way can allow scaling to a very large extent. Facebook, Instagram, PayPal all were able to scale React apps to a very large extent. 

Angular on the other hand comes with most of the things baked in, so it is very easy to scale an Angular app with its structure and CLI.

## 📚 Learning Curve

React is very easy to learn if you already have JavaScript and ES6 knowledge as it does not introduce a lot of new concepts

Angular on the other hand introduces a lot of new concepts so you have no options to learn them in order to develop an app using Angular. So definitely Angular is hard when it comes to Learning.

## ⚙️ SEO 

SEO(Search Engine Optimization) is very crucial for website traffic. When it comes to SEO both React and Angular are bad at it as both of them use Client-Side Rendering which means the HTML that needs to indexed is visible only after the JavaScript is loaded.

But it's much easier to set up server-side rendering with React than with Angular – and server-side rendering is better for SEO

## 📈 Popularity among developers


-  As per Google Trends Results, React has more Interest over time compared to Angular

![Screenshot 2020-12-31 at 1.23.41 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609358025911/4oSSwWtXa.png)

- As per Stack Overflow Survey 2020, React.js is a more loved framework/library compared to Angular
![Screenshot 2020-12-29 at 8.18.10 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1609358045827/nAqYv2uFA.png)

- React has ⭐ 161K Stars on Github whereas ⭐ Angular has 69.2K at the time of writing this blog.

## 🏢 Companies using React and Angular

### React

- Facebook
- Instagram
- Netflix
- WhatsApp
- Uber
- Twitter 
- Medium etc

### Angular

- Google
- Nike
- Forbes
- Upwork
- HBO
- Apple etc

## 🤔 Which one to choose?

Both are awesome technologies and you can't go wrong with any of the two as they are evolved and the community around them is insane.

If you are new to JavaScript and you want to learn quickly and get a job quickly then go with **React**

If you have the time to learn difficult concepts and you want an app that scales easily then go with **Angular**

-> I personally choose **React** over Angular due to its simplicity, Virtual DOM, rendering optimizations, React-Native(allows us to build native mobile apps using React and JavaScript), and flexibility that React provides. 


Thank you for reading this far. Do share your valuable suggestions and feedback.
I will see you in my next article.