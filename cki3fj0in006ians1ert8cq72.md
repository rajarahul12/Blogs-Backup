## Best Practices for Securing Websites from Attacks

In this article, I will be discussing some of the common attacks on websites and some preventive measures that can be followed to avoid them. These are the things that every Web Developer should take into consideration while building a website. Without any further due, Let's get started.

### 1\. Avoid SQL Injections

SQL Injection is a code injection technique used to <span id="rmm"><span id="rmm"></span></span> attack data-driven applications. These are some common attacks on websites. A common example is dropping the table from the database. So, take an example as a user is logging into the website and along with user id he added an SQL Statement DROP Table users; at the end of our query where we are accessing the database. This is a valid SQL Statement and if this is taken as an input then the table gets deleted.

And also another common Injection is adding 1 == 1 at the end of the query where we are validating the user. This is always true and the user gets logged in if the user id is known.

This is a great resource that explains visually how [SQL Injection Works ](https://www.hacksplaining.com/exercises/sql-injection).

##### **PRECAUTIONS**

_Parameterize Queries_ : Use libraries like [Knex.js](https://knexjs.org/) or other ORM’s (Object Relational Mappers) for queries.

### 2\. Third-Party Libraries

Do not use 3rd Party Libraries without checking that they are secure or not. For example the modules or packages that you download using npm or yarn make sure that they are secure before using them.

##### **RESOURCES**

The best ways to check them is by using a module named *nsp*. It audits the package.json file and checks whether the installed packages are prone to vulnerabilities or not.


```
npm install -g nsp
nsp check
``` 


The other module is *synk*. It audits the node_modules directory

**NOTE:** With npm 6 we will be able to check for vulnerabilities soon after installing the modules. If vulnerabilities are found use **_npm audit fix_** to fix all the vulnerabilities.

### 3\. Logging

Inefficient Logging allows attackers to attack systems/servers so that they can tamper or extract or destroy the data which is very valuable.

##### **RESOURCES**

For safe logging in your servers use packages like *Morgan* or *Winston* that provide a safe and secure way for logging.

### 4\. Always use HTTPS

Websites using HTTP instead of HTTPS are prone to more attacks. If you are using HTTP, immediately migrate to HTTPS. Because HTTPS sites use SSL/TLS certificates that use high-grade ciphers to create a tunnel called HTTPS, this encrypts information between client and server while we are making HTTP requests.

##### **RESOURCES**

Try [LetsEncrypt](http://www.letsencrypt.org) that provides free HTTPS certificates for your websites.

Also, try [Cloud Flare](https://www.cloudflare.com/) that uses CDN’s to deliver our files to the browser along with HTTPS requests. Cloud Flare also protects your site from DDOS(Distributed Denial of Service Attack) that occurs when a ton of computers tries to send requests to a server.

### 5\. XSS & CSRF

**_XSS: Cross-Site Scripting_**
XSS enables attackers to inject client-side scripts into web apps viewed by other users. XSS may be used by attackers to bypass access controls. Cross-site scripting carried out on websites accounted for roughly 84% of all security vulnerabilities.

This is a great resource that explains visually how[XSS works](https://www.hacksplaining.com/exercises/xss-stored).

XSS is mostly used for Session Hijacking.

**_CSRF: Cross-Site Request Forgery_**
CSRF attack forces the user to execute unwanted actions on web applications in which they are currently authenticated. If the victim is a normal user, a successful CSRF attack can force the user to perform state-changing requests
like transferring funds, changing their email address, and so forth. If the victim is an administrative account, CSRF can compromise the entire web application.

This is a great resource that explains visually how [CSRF works](https://www.hacksplaining.com/exercises/csrf).

Both of these attacks can be used to steal the cookies of a user for a particular site.

##### **PRECAUTIONS**


- Sanitize Inputs: Accept only the type of input you want.
- Don’t use eval() functions
- Don’t use document.write()
- Use Content Security Policy Headers
- Use Secure + HTTP Only Cookies
- npm CSRF package can also be used to avoid CSRF attacks.

### 6\. Code Secrets

Never expose sensitive information. Always use Environment Variables to inject passwords and other sensitive information into the Front End code. A good practice is to create a .env file in your project folder that contains all the environment variables and we can
import from that file whenever we need.

##### **SUGGESTION**

Never commit secret data such as API keys / Passwords and other sensitive information to GitHub. Because these will be visible in your commit history even though you have changed them.

### 7\. Secure Headers

Always use secure headers. In the network Tab of your Developer Tools of a Browser, you will be able to see the headers whenever a request is made.
So securing them will hide a lot of information about the website like the type of server you are using, cookies are being used or not and a lot more.

##### **EXAMPLE**

For the express app, there is a middleware called helmet that helps us to secure the headers.

```
npm install helmet
const app = express()
app.use(helmet())
``` 


This only shows the information that is required by the browser and hides the rest of the information.

### 8\. Access Control

Restrict the actions that authenticated users can do on a website. Follow the Principle of Least Privilege.

##### **SUGGESTION**

Use CORS (Cross-Origin Resource Sharing) for all your servers and API’s that restricts the requests that can be made to the server. Only authenticated users can make requests to the server. We can also white list the sites from which requests can be made.

**NOTE:** This is the way API’s work(like GitHub API, Google Maps API). They validate the users based on API keys and only users with a valid API key can request the data.

### 9\. Data Management

Data is very crucial and securely storing the data is important. Create Backups for the data in case something goes wrong. Try to Encrypt data during in transit between server and client.

##### **RESOURCES**

Use packages like bcrypt, scrypt and Aragon2 for password hashing.

Use software like pgcrypto for encrypting data in the database

### **10\. Limit the Requests**

If there is no load-balancing for the server and some of the attackers try to get down the server then multiple requests to the server can do that. So limiting concurrent requests to the server helps a lot for basic servers with a single instance and no load-balancing implemented.

##### **RESOURCES**

Use packages such as rate limiter that limits the rate at which requests to the server can be made.

### NOTE

[OWSAP](https://www.owasp.org/index.php/Main_Page)(Open Web Application Security Project) produces freely-available articles, methodologies, documentation, tools, and technologies in the field of web application security.

<span class="ki fh bn kj kk kl"></span><span class="ki fh bn kj kk kl"></span><span class="ki fh bn kj kk"></span>

Thank you for reading this far. If you like this post, please share and comment.