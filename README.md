Download Link: https://assignmentchef.com/product/solved-cs142-project4-page-generation-with-reactjs
<br>
You should already have installed Node.js and the npm package manager your system. If not, follow the <a href="https://web.stanford.edu/class/cs142/install.html">installation instructions (install.html) </a>now.

Create a directory project4 and extract the contents of <a href="https://web.stanford.edu/class/cs142/downloads/project4react.zip">this zip le (downloads/project4react.zip)</a> into the directory. The zip le contains the starter les for this assignment.

<a href="https://eslint.org/">This assignment requires many node modules the contains the tools (e.g. Webpack (https://webpack.js.org/)</a><a href="https://eslint.org/">, </a><a href="https://eslint.org/">Babel (https://babeljs.io/)</a><a href="https://eslint.org/">, </a><a href="https://eslint.org/">ESLint</a>

<a href="https://expressjs.com/">(https://eslint.org/)) needed to build a ReactJS (https://reactjs.org/) web application as well as a simple Node.js web server (ExpressJS</a>

<a href="https://expressjs.com/">(http://expressjs.com/)</a><a href="https://expressjs.com/">) </a><a href="https://expressjs.com/">to serve it to your browser. These modules can be fetch by running the following command in the </a><a href="https://expressjs.com/">project4</a> directory:

The command will fetch around 600 node modules using around 110 megabytes of space into the subdirectory node_modules .

We can use npm to run the various tools we had it fetch. As can be seen in the “scripts” property of the package.json le, the following run commands are availble:

npm run lint – Runs ESLint on all the project’s JavaScript les. The code you submit should run ESLint without warnings.

npm run build – Runs <a href="https://webpack.js.org/">Webpack (https://webpack.js.org/)</a> using the con guration le webpack.config.js to package all of the projects JSX les

into a single JavaScipt bundle in the directory compiled .

<a href="https://webpack.js.org/api/cli/#watch-options">npm run build:w</a><a href="https://webpack.js.org/api/cli/#watch-options"> – Runs Webpack (https://webpack.js.org/) like the “run build” command except it invokes webpack with –watch</a>

<a href="https://webpack.js.org/api/cli/#watch-options">(https://webpack.js.org/api/cli/#watch-options) so it will monitor the React components and regenerates the bundle if any of them</a> change. This option is useful for development so changes made to components can be picked up by simply refreshing the browser to load the newly updated bundle. Otherwise you need to remember to run “npm run build” after every change.

Your solutions for all of the problems below should be implemented in the project4 directory.

This project uses <a href="https://reactjs.org/">ReactJS (https://reactjs.org/),</a> a popular framework for building web applications. The project’s goal is to get you enough up to speed with ReactJS and the cs142’s coding conventions that you will be able to build a web application with it in the next project.

In order to fetch our web app via the HTTP protocol, we use a simple Node.js web server that can be started with the command from the project4 directory:

<a href="http://localhost:3000/">All the les in the </a><a href="http://localhost:3000/">project4</a><a href="http://localhost:3000/"> can be fetched using an URL starting with http://localhost:3000 (http://localhost:3000)</a><a href="http://localhost:3000/">. </a><a href="http://localhost:3000/">Click on http://localhost:3000 (http://localhost:3000) to verify your web server is running. It should serve the le </a><a href="http://localhost:3000/">index.html</a><a href="http://localhost:3000/"> to your browser.</a>

We recommend you con gure you development environment to run webpack in watch mode so you will need to run the node web server and webpack when building and testing your project. You could do this by running the programs in di erent command line windows. Syntax errors get detected and reported by Babel so the output of webpack is useful. If you are running on a system with a unix-like shell like MacOS. The command:

runs the web server in background and the webpack in foreground within a single window.

On Windows you can start the web server in background and webpack in foreground with the two Windows commmands:

You can stop the background webserver with the command:

In this project we require that you use the model, view, controller pattern described in class. There are many ways of organizing code under this pattern so we provide an example that both demonstrates some basic ReactJS features as well as showing the le system layout and module pattern we would like you to follow in your projects.

<a href="http://localhost:3000/getting-started.html">You should start by opening the example in your browser by navigating to the URL http://localhost:3000/getting-started.html</a>

<a href="http://localhost:3000/getting-started.html">(http://localhost:3000/getting-started.html)</a><a href="http://localhost:3000/getting-started.html">. </a><a href="http://localhost:3000/getting-started.html">The page displays examples of ReactJS in action. The HTML in </a><a href="http://localhost:3000/getting-started.html">getting-started.</a>html provides a div for

ReactJS to draw the app into and a script tag include the app’s JavaScript bundle compiled/gettingStarted.bundle.js . The webpack con g le <a href="http://localhost:3000/webpack.config.js">webpack.config.js (http://localhost:3000/webpack.config.js)</a> directs that this bundle be created from the ReactJS le gettingStarted.jsx , a JSX program that renders the ReactJS component named Example into the div in getting-started.html.

To support reusable components, we adopt a le organization that co-locates the ReactJS component and its associated CSS stylesheet in a subdirectory of a directory named components . The Example component is located in the les components/example/{Example.jsx,Example.css} .

You should look through the les invoked in the getting-started.html view ( getting-started.html , gettingStarted.jsx , components/example/{Example.jsx ) since it shows the JavaScript and JSX statements needed to run an ReactJS web application along with explanatory

comments. You should use this pattern and le naming convention for the other components you build for the class.

Model data is typically fetched from the web server which retrieves the data from a database. To avoid having to setup a database for this project we will give you an HTML script tag to load the model data directly into the browser’s DOM from the local le system. The models will appear in the DOM under the property name cs142models . You will be able to access it under the name window.cs142models in an ReactJS componment.

<h1> Problem 1: Understand and update the example view</h1>

You should look through and understand the getting-started.html view and the Example component. To demonstrate your understanding do the following:

<ol>

 <li>Update the model data for the Example component to use your name rather than “Unknown name”. You should nd where “Unknown name” is and replace it.</li>

 <li>Replace the contents of the div region with the class motto-update in the Example component with some JSX statements that displays your name and a short (up to 20 characters) motto. Like the user’s name, the initial value for motto should come in with the model data. You must include some styling for this display in css .</li>

 <li>Extend the display you did in the previous step so it allows the user to update the motto being displayed. The default value should continue to be retrieved from the model data.</li>

</ol>

<h1> Problem 2: Create a new component – states view</h1>

Create a new component view that will display the names of all states containing a given substring. Your view must implement an input eld which accepts a substring. The view will display in alphabetical order a <strong>list</strong> of all states whose names contain the given substring (ignoring di erences in case). For example, the view for the substring of “al” should list the states Alabama, Alaska, and California. The page should also display the substring that was used to lter the states. If there are no matching states then the web page should display a message indicating that fact (rather than just showing nothing). All states should be displayed when the substring is empty.

As in Problem #1 we provide you the model data with states. It can be accessed via window.cs142models.states after it is included with:

See states.js for a description of the format of the states data.

To help you get started and guide you to the le naming conventions we want you to use we provided a le p2.html that will load and display the bundle compiled/p2.bundle.js which is generated by webpack from p2.jsx which displays the React component States . You can open this le in your browser via the URL <a href="http://localhost:3000/p2.html">http://localhost:3000/p2.html (http://localhost:3000/p2.html)</a><a href="http://localhost:3000/p2.html">.</a>

The les you will need to implement are:

components/states/States.jsx – The ReactJS Component of your states component. components/states/States.css – Any CSS styles your component needs. <strong>You must include some styling for your state list here.</strong>

<h1>Problem 3: Personalizing the Layout</h1>

Create a ReactJS component named Header that will display a personalized header at the top of a view. Add this header to all ReactJS web apps in your assignment ( gettingStarted.jsx , p2.jsx , p4.jsx , p5.jsx ). Note that you <strong>should not </strong>replace the section from part 1 (your name and motto). That section should be separate from your header. Use your imagination and creativity to create a header that is “uniquely you”. This can include additional images, graphics, whatever you like. You can extend the JSX/JavaScript in the components but you may not use external ReactJS Components or JavaScript libraries such as JQuery. Be creative!

The les you will need to implement are:

<a href="https://reactjs.org/docs/react-component.html">components/header/Header.jsx</a><a href="https://reactjs.org/docs/react-component.html"> – The ReactJS Component of your header component. This is de ned a class Header of type React.Component (https://reactjs.org/docs/react-component.html)</a><a href="https://reactjs.org/docs/react-component.html">. </a>components/header/Header.css – Any CSS styles your component needs. <strong>You must include some styling for your header here.</strong>

Note: gettingStarted.jax should have a personalized header from Problem 3 at he top of the page and the section with the motto from Problem 1.2 right below it. All other page views ( p2.html , p4.html and p5.html ) should have your personalized header from Problem 3.

<h1> Problem 4: Add dynamic switching of the views</h1>

Create a p4.html and a corresponding JSX le p4.jsx that includes both view components (the Example and States components). The p4.jsx needs to implement an ability to switch between the display of the two components. When a view is displayed there should be a button above it that switches to display the other view. For example, when the States view is displayed the button above it should read “Switch to Example,” and when pushed the States should disappear and the Example view should be displayed.

For this problem you will need to create the les above as well as modify the webpack con guration le webpack.config.js to build a le compiled/p4.bundle.js that you can uses in p4.html le. Note that if you are using Webpack with –watch (i.e. npm run build:w), you will need to

restart it after changing code&gt;webpack.con g.js.

<h1> Problem 5: Single page app</h1>

Although the approach taken in Problem 4 allows you to switch between the two views, it does not allow you to bookmark or share a URL pointing at a particular view. Even doing a browser refresh event causes the app to lose track of which view was being displayed.

We can address this de ciency by storing the view information into the URL. <a href="https://reacttraining.com/react-router/">React Router (https://reacttraining.com/react-router/) </a>provides this functionality for ReactJS. For this problem make a copy of your p4.html solution into a le named p5.html and copy your p4.jsx into a le named

p5.jsx . Convert the code to use <a href="https://reacttraining.com/react-router/">React Router (https://reacttraining.com/react-router/)</a> to switch between the two component views. You should have a

<strong>styled toolbar-like control</strong> (simple plain text links are not su    cient) that will allow the user to switch between the example and states component views.

Since this is the rst extensions from the core ReactJS we import, we provide you with step-by-step instructions.

<ol>

 <li>The project’s json speci es react-router so the npm install command already fetched it for us. We do need to explicitly import it into our p5.jsx le. Add the following import line:</li>

</ol>

The line uses the JavaScript <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/importinport">import (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/importinport)</a> statement to <a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/api/HashRouter.md">bring in the ReactJS components from React Router: HashRouter (https://github.com/ReactTraining/react-router/blob/master/packages/react</a><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md">router-dom/docs/api/HashRouter.md)</a><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md">, </a><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md">Route (https://github.com/ReactTraining/react-router/blob/master/packages/reactrouter/docs/api/Route.md), and </a><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/api/Link.md">Link (https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/docs/api/Link.md)</a>. The HashRouter module of React Router uses the fragment portion of the URL for storing infomation. So we can make p5.html#/states mark showing the States view while p5.html#/example speci es the Example component view.

<ol start="2">

 <li><a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md">The most common way of using React Router is to conditially render the view we want based on the current URL. It is the Route</a></li>

</ol>

<a href="https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md">(https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Route.md) component that implem</a>ents this condition rendering when placed inside a HashRouter element like:

which would render the States component if the URL had #/states and the Example component if the URL had #/example .

<ol start="3">

 <li>Although we could use hyperlinks (i.e. &lt;a tags) to switch views react router recommends using the Link component to generated the hyperlinks.</li>

</ol>

generates a hyperlink with href=”#/states” and the strings “States” in it.

<h1> Style</h1>

These points will be awarded if your solutions have proper MVC decomposition and follow the style guidelines discussed in lecture and section. <strong>Note that you should not directly manipulate the DOM in your code.</strong> In addition, your code and templates must be clean and readable. Remember to run ESLint before submitting. ESLint should raise no errors.

<h1> Deliverables</h1>

<strong>After implementing part 5, make sure parts 1 through 4 still work!</strong>

Use the standard class <a href="https://web.stanford.edu/class/cs142/submit.html">submission mechanism (submit.html)</a> to submit the entire application (everything in the project4 directory).

Designed by Raymond Luong for CS142 at Stanford University

Powered by <a href="https://getbootstrap.com/">Bootstrap (http://getbootstrap.com/) </a>and <a href="https://jekyllrb.com/">Jekyll (https://jekyllrb.com)</a> – <a href="https://web.stanford.edu/class/cs142/website.html"><strong>learn more</strong></a><a href="https://web.stanford.edu/class/cs142/website.html"> (website.html)</a>