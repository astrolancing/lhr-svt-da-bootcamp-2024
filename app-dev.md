### **Reinforcement Learning Bootcamp Overview**
**Duration:** 4 Weeks 
**Level:** Beginner  
**Technologies:** JavaScript, TypeScript, Next.js, React, React Native, 
**Goals:**
- Become comfortable with JavaScript
- Understand key concepts of web and mobile programming
- Gain practical experience in developing web and mobile applications
- Use popular web/mobile libraries and frameworks (Next.js, React Native)

---

### **Week 1: Introduction to Web Programming**

#### **Topics Covered:**
- Introduction to JavaScript
  - Installing Node.js
- Overview of Web Programming
  - Key concepts: HTTP, HTML, CSS, async, React, functional programming

#### What is the web?

The web is pretty complex. We interact with it everyday, but among the most complex real-world problems businesses face are dealing with the web and its assortment of issues. How do we scale to millions of user? How do we even 'communicate' with them, how does a browser work? How does the internet even function? We'll briefly cover all those concepts, but a Networking class will go deeper if you're wanting more. 

##### The Internet
The internet is roughly the mass linking of the computers through a physical layer, literally wire in the ground, using protocols such as UDP and TCP. The physical layer is commonly accessed though through WiFi among other technologies which are transmitted via electromagnetic radiation. The UDP and TCP protocols set the standard for communication so we can actually understand how to send and read data using packets or small, fixed-length groups of data. 

##### The Web
The internet can be used for a wide variety of applications like email, FTP, VoIP, etc. These applications use their own protocols over the internet. The web is an application and its protocol is primarily HTTP(S). HTTP is simple: a user/client requests a specific resource, the server/service will provides that resource in plaintext. 

##### DNS
Okay, how do I find that server/service though as a user? DNS is the important technology that essentially acts a registrar. It links domains, i.e. google.com, to IPs. Whenever you go to google.com, your requests actually being forwarded to that specific IP. 

##### Browsers
Plaintext is cool but it isn't gonna suffice for a complex application. What if I want to click a button? Browsers, or the application users use to view web pages, implement various technologies such that servers/services' plaintext can take advantage of these technologies to stylize, add interactivity, and create complex experinces. These technologies are primarily HTML, CSS, and JavaScript. We'll learn all three. 

##### HTML
HTML is used to structure the content of the web page. Viewing HTML (with a browser that has implemented it) without CSS and JavaScript is the exact same as the original plaintext. It's useful because it lets use identify content from CSS and JavaScript. 

##### CSS
CSS is used to stylize web pages. It works by providing an identifier, linked to the HTML, and applying styles like color, size, etc. 

##### JavaScript
JavaScript is an actual programming language and is primarily used on the web to add interactivity. For example, it is very difficult to create a game without JavaScript on the web. It is a weakly-typed, dynamic programming language.

#### Wow that is a lot of technologies
It certainly already is, and is the biggest hurdle regarding web programming. These technologies on their own are not particulary complex, but combining dozens of technologies (there are many more to learn as well not mentioned here!) can be especially difficult. 

Here are a couple resources to look at it:

- https://www.w3schools.com/html/default.asp
- https://www.w3schools.com/css/default.asp
- https://www.w3schools.com/js/default.asp

W3 provides many, many tutorials on all these technologies without any setup. We strongly recommend going through the beginning sections of each link above if you are not familiar with these technologies, completing all sections is not required. HTML, CSS, and then JS. 

- https://developer.mozilla.org/en-US/docs/Web/CSS
- https://developer.mozilla.org/en-US/docs/Web/JavaScript

Documentation for CSS and JavaScript

#### Let's start programming!

After reading the JS tutorials, let's install a code editor, [VSCode](https://code.visualstudio.com/). VSCode is light-weight, customizable, and recommended. 

Let's also install Node.js. Node.js, briefly, is essentially the engine that executes JavaScript in the browser, but can be used now on any platform. We recommend [NVM]("https://github.com/nvm-sh/nvm"), node version manager. There's also a [windows]("https://github.com/nvm-sh/nvm") version.

Follow your OS's NVM guide to install the latest, recommended version of Node.js. It should look like, in the terminal,
```bash
nvm install 20
nvm use 20
```

Let's create a JS file then in VSCode and do a couple exercises. 
```js
// file.js
// Exercise 1, write a calculator!

const calculator = (a, b, operation) => {
    // function here!
}

console.log(calculator(4, 5, "add"))  // should probably output 9
console.log(calculator(4, 5, "mult")) // should probably output 20
console.log(calculator(4, 5, "sub"))  // should probably output -1

// Exercise 2, use your knowledge to create an HTML file with CSS and possibly JavaScript using Node.js, then open that HTML file with a browser. 
const fs = require('fs');

const myPage = () => {
    fs.writeFile("page.html", plaintext goes here);
}

// I recommmend using string literals like
const data = `<html>
    <body>
        <p>Hello, world!</p>
    </body>
</html>
`

```

#### Next.js
Web programming framework. Follow https://nextjs.org/docs/getting-started/installation