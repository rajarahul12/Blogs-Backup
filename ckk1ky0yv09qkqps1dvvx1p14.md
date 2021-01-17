## Authenticate users using Google SignIn in a React App

Google SignIn is one of the safest ways of handling authentication inside your app. In this blog, I'll show you how you can easily integrate Google SignIn into a React App in **5 Steps**.


##  💻 DEMO

![SignIn.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1610910534953/U5jHdc24f.gif)


### Step 1
-> Adding Heading, Image, and SignIn with Google Button

*I have downloaded the illustration from  [unDraw](https://undraw.co/search) and added it to the assets folder*  


```
// App.js
// Importing the illustration from the assets folder
import { ReactComponent as Login } from "./assets/signin.svg";
import "./App.css";

function App() {

  return (
    <div className="app">
          <h4>SIGNIN</h4>
          <Login className="app__loginSvg" />
          <button className="app__buttonDiv">
            <img className="app__loginImg" 
             alt="Google sign-in" 
             src="https://i.ibb.co/qNdyvc7/google.png"
            />
            <div>SignIn with Google</div>
          </button>
    </div>
  );
}

export default App;
``` 


### Step 2
-> Let's add some CSS


```
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

.app h4 {
  margin-top: 50px;
  text-align: center;
  color: #282c34;
}

p {
  color: #282c34;
}

.app__loginSvg {
  margin-top: 100px;
  height: 300px;
}

.app__buttonDiv {
  margin-top: 100px;
  display: flex;
  align-items: center;
  background-color: #282c34;
  color: white;
  border-radius: 3px;
  padding: 10px;
  border: none;
  outline: none;
  cursor: pointer;
  box-shadow: 0 4px 8px 0 rgba(65, 63, 63, 0.2),
    0 6px 20px 0 rgba(65, 63, 63, 0.19);
}

.app__loginImg {
  margin-right: 10px;
  width: 20px;
  height: 20px;
}

.app__buttonDiv div {
  font-size: 15px;
}

``` 

### Step 3
-> Create a firebase project


- Goto  [Firebase](https://console.firebase.google.com/u/2/) and click *Add Project*
- Give your Project a name click *Continue*
![Screenshot 2021-01-18 at 1.00.00 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610911806086/pbdk__yEy.png)
- Enable/Disable Analytics based on your preference and click *Continue*
- After the project is created we need an app for the web platform. Click on the Web Icon and give your web app a name and then click on *Register App* and then *Continue to Console*
![Screenshot 2021-01-18 at 1.02.31 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610911959806/9h1x8oa2X.png)
- Go to Authentication Tab and enable Google Sign-in under the Sign-in Method
![Screenshot 2021-01-18 at 1.07.44 AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610912270422/7jo6GtN2N.png)
- Copy the config as shown below and then create a new file **firebase.js** inside the src folder of your React app and paste the config.

![config.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1610912579547/PsWT7CjML.gif)


### Step 4
-> Add and configure firebase inside the React App


- Install the Firebase SDK 
> npm install firebase
- Import and configure firebase auth and Google Auth Provider

```
// firebase.js
import firebase from "firebase";

// Config from firebase console
// PS: This config won't work - Create your own
const firebaseConfig = {
  apiKey: "AIzaSyAGA3vzfaRwnztTuZLVm87I-90YsK3vMf8",
  authDomain: "react--signin-784bc.firebaseapp.com",
  projectId: "react--signin-784bc",
  storageBucket: "react--signin-784bc.appspot.com",
  messagingSenderId: "325335555788",
  appId: "1:325335555788:web:f918254262d0d13ad12c69",
};

// Initilizing firebase 
firebase.initializeApp(firebaseConfig);


const auth = firebase.auth();
// Configuring Google Auth Provier
const GoogleSignIn = new firebase.auth.GoogleAuthProvider();

// Exporting firebase authentication and GoogleAuthProvider
export { auth, GoogleSignIn };

``` 

### Step 5
-> SignIn and SignOut functions - Setting the state to user data when signed in and to null if signed out


```
// State for storing user data
const [user, setUser] = useState(null);

// Should be called when SignIn with google is clicked
const handleSignIn = () => {
  auth
    .signInWithPopup(GoogleSignIn)
    .then((result) => {
      setUser(result.user);
    })
    .catch((error) => {
      alert(`Failed to SignIn : ${error.message}`);
    });
};

// Should be called when SignOut is clicked (We are Yet to add that button)
const handleSignOut = () => {
  auth.signOut();
  setUser(null);
};
``` 

**Entire App.js**

```
import { auth, GoogleSignIn } from "./firebase";
import { ReactComponent as Login } from "./assets/signin.svg";
import "./App.css";
import { useState } from "react";

function App() {
  // State for storing user data
  const [user, setUser] = useState(null);

  // Should be called when SignIn with google is clicked
  const handleSignIn = () => {
    auth
      .signInWithPopup(GoogleSignIn)
      .then((result) => {
        setUser(result.user);
      })
      .catch((error) => {
        alert(`Failed to SignIn : ${error.message}`);
      });
  };

  // Should be called when SignOut is clicked
  const handleSignOut = () => {
    auth.signOut();
    setUser(null);
  };

  return (
    <div className="app">
      {/* Conditionally rendering JSX based on state - If user is present  */}
      {!user ? (
        <>
          <h4>SIGNIN</h4>
          <Login className="app__loginSvg" />
          <button onClick={handleSignIn} className="app__buttonDiv">
            <img
              className="app__loginImg"
              alt="Google sign-in"
              src="https://i.ibb.co/qNdyvc7/google.png"
            />
            <div>SignIn with Google</div>
          </button>
        </>
      ) : (
        <>
          <h4>Sign Out</h4>
          <p>{`Hello ${user?.displayName} 👋`}</p>
          <button className="app__buttonDiv">
            <div onClick={handleSignOut}>Sign Out</div>
          </button>
        </>
      )}
    </div>
  );
}

export default App;

``` 

**Yup, this is all need to integrate Google SignIn into a React app. All the user's data can be seen in the Authentication tab of the Firebase console.**

![Screenshot_2021-01-18_at_1_24_45_AM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610913321790/_Ag5m59sY.png)

-> Complete Source Code can be downloaded from my  [Github Repository](https://github.com/rajarahul12/google-signin-react)  

Thank you for reading, I would love to connect with you at  [Twitter](https://twitter.com/coder_rahul)  |  [Instagram](https://www.instagram.com/coder_rahul).

Do share your valuable suggestions, I appreciate your honest feedback!

**You should definitely check out my other Blogs:**

-  [React vs Angular: Which one to choose for your Web App?](https://rajarahul.com/react-vs-angular) 

-  [Embed an Instagram post in a React App](https://rajarahul.com/embed-instagram-post) 

-  [What is React.js and Why is React.js created? ](https://rajarahul.com/react-js) 

PS: By now you might have noticed that I am a React fanboy. Yes, I am.
Which technology do you love? Let me know in the comments 💬

See you in my next article, Until then Bye 👋