## Embed an Instagram post in a React App

Instagram is one of the most used social media platforms in recent times. And the content that is available is very informative and sometimes you want to share it with others from your web app. In this article, I will show exactly how you can embed an *Instagram post* in a React app.

Let's start coding it right away.

### Time to code

-> Create a new react project or you can use the existing react project as well. Then do npm start to start the react app locally.


```
npx create-react-app instagram-embed
cd embed-instagram
npm start
``` 

This will run the react app locally on *localhost:3000*

-> Remove all the starter code from *App.js* and keep it simple like below.

```
import './App.css';

function App() {
  return (
    <div className="App">
      <h1>Instagram Embed</h1>
    </div>
  );
}

export default App;

``` 

-> Next step is to install a package called  [react-instagram-embed](https://www.npmjs.com/package/react-instagram-embed) 

```
npm i react-instagram-embed
```

-> Now let's import add the code to embed the Instagram post

```
// import statement
import InstagramEmbed from "react-instagram-embed";
```

```
// Code to embed a post
<InstagramEmbed
  url=""
  clientAccessToken=""
  maxWidth={500}
  hideCaption={false}
  containerTagName="div"
  injectScript
/>
``` 
In the above code, we have to pass two props to **InstagramEmbed** component  in order to see the post

- **url**: URL of the post that you want to embed
- **clientAccessToken**: Instagram Client Access Token

### Obtaining the URL

Go to  [Instagram](https://www.instagram.com/), Open the post that you want to embed, and copy the URL of that post and pass this value to the **url** prop.

```
<InstagramEmbed
  url="https://www.instagram.com/p/CH9gbEEFqYj/"
  clientAccessToken=''
  maxWidth={500}
  hideCaption={false}
  containerTagName="div"
  injectScript
/>
```
At this point, you won't be able to see the post as we have not passed the accessToken

### Obtaining the client Access Token

Go to  [Facebook for Developers](https://developers.facebook.com/apps), Login and create a new app in order to obtain the AccessToken.

- Click on *Create App* and select *Something Else* for this demo purpose.

![Screenshot 2020-11-28 at 9.21.29 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606578722377/Ot3bvBpK7.png)

- Then it will prompt for an *App Display Name*, provide a name for your app and click on *Create App*

- Once the app is created Navigate to **Settings > Advanced**. In the Security section, there will a **Client Token**. Copy the client token and also the **App ID
**


![Screenshot_2020-11-28_at_9_24_42_PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606579836224/65ECn-QyU.png)

**clientAccessToken** is a combination of *App ID* and *Client Token* 

**{app-id}|{client-token}**

Ex: 123|456

- Pass this value to the **clientAccessToken** prop.


```
// This is a fake token. Don't try to use it :)
// Create your own and use it
<InstagramEmbed
  url="https://www.instagram.com/p/CH9gbEEFqYj/"
  clientAccessToken='415948662920177|1e6b807a0033b7a76afc91317725c26b'
  maxWidth={500}
  hideCaption={false}
  containerTagName="div"
  injectScript
/>
``` 

Now you should be able to see the Instagram post in your React App.

![Screenshot 2020-11-28 at 9.31.52 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1606579326903/WY7_C6trl.png)


Complete App.js code


```
import './App.css';
import InstagramEmbed from "react-instagram-embed";

function App() {
  return (
    <div className="App">
      <h1>Instagram Embed</h1>
      <div style={{display:"flex",justifyContent:"center"}}>
        <InstagramEmbed
          url="https://www.instagram.com/p/CH9gbEEFqYj/"
          clientAccessToken='415948662920177|1e6b807a0033b7a76afc91317725c26b'
          maxWidth={500}
          hideCaption={false}
          containerTagName="div"
          injectScript
        />
      </div>
    </div>
  );
}

export default App;
``` 

This is how you can embed Instagram posts in your react apps. That's it!
Simple, isn't it? Hope this tutorial has helped.

You can find all the code in my  [GitHub Repository](https://github.com/rajarahul12/react-instagram-embed-example). Drop a *star* if you find it useful.

Thank you for reading, I would love to connect with you on  [Twitter](https://twitter.com/coder_rahul)  |  [Instagram](https://www.instagram.com/coder_rahul/)  |  [LinkedIn](https://www.linkedin.com/in/raja-rahul/) .

Do share your valuable suggestions, I appreciate your honest feedback!

### Resources:


-  [react-instagram-embed](https://www.npmjs.com/package/react-instagram-embed) 
-  [Instagram Client Access Tokens](https://developers.facebook.com/docs/instagram/oembed/#client-access-tokens)
-  [Facebook for Developers](https://developers.facebook.com/apps)

I will see you in my next article, Peace ✌️ 