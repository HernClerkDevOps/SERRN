## Standards for ReactJS
React is a front end UI library created by the Facebook/Instagram team that leverages the use of JSX in order to be compiled anywhere and can be used on an array of different platforms such as the web, iOS, Android, and VR systems. ReactJS is the web-based library that uses a VirtualDOM in order to render transpiled JSX components. The VirtualDOM allows for a much faster rendering process and thus makes React a great choice for object-heavy user interfaces.

#### The typical modules used are:
- react-router (creating routes)
- react-router-dom
- redux
- redux-thunk (for creating asynchronous actions (HTTP requests))
- react-redux
- redux-logger (for logging changes in Redux state)
- axios (ajax handler with similar syntax as angular.js)
- material-ui or @material-ui/core (Suite of React components based on Google's Material Design)
- react-moment, moment (for handling the rendering/manipulation of dates)



### Goals

React can be used in many capacities, including projects that need to be developed quickly. Most importantly, web projects that require the use of repetitive elements should be using React unless there is another variable in the project that would not leverage React's benefits.

React should:

 - Render the page quickly.
 - Make use of repetitive elements and group them as reusable components.
 - Take advantage of immutable state.
 - Leverage code portability if an application needs to run on more than one platform.
 - Break components by logically separated tasks.
 - Share as little data as possible between components.
 - Take advantage of Redux when data or state must be shared between components.
 - Take advantage of being a single page application

While being:

 - Fast, efficient, and perform well.

### Getting Started with React

Keep in mind that some features in modern frameworks may not work correctly in Internet Explorer.

##### Some note-worthy rules:
 - Do not access the DOM
 - When creating HTTP GET requests from more than one component, use Redux
 - Use React-Router if your application needs more than one route
 - All component classes must begin with a capital letter
 - Create a CSS file for each component
 - UI controls should only be modified using props and never by accessing the DOM directly
 - Minimize CCSS conflicts, because CSS classes are global even if they're in separate files
 - Use pure functions to modify Redux reducers
 - Use ES6/7 functions ex: map, reduce, filter
 - Use component lifecycle hooks only when necessary
 - Finally, settings and configuration options (e.g. paths to services, debug flags, duration settings, minimum or maximum values, etc.) are common things to set in a centralized, distinct place.

Bottom line, please understand what React does and how it works. The documentation explains it very well.

##### Selection of Third Party Code


Selection of a library or framework is never an easy task. Things that should be considered include:

- Is it on GitHub? Is it a package in NPM? If it isn't, don't use it.
- When was the last commit date? Was it more than a year ago?
- How many commits has this project had?
- How many contributors are there to this project? Maintainers? Do they take care of the project's issues?
- How many stars does this project have?
- How much of this project is actually needed?
- What is its license? Please refrain from Copyrighted and AGPL libraries as much as possible.

##### Usage of Third Party Code

Third party code should be included as-is and:

 - Be installed via NPM
 - Treated as it may be updated (i.e. versions) at some point in the future.
 - Should **never be modified** unless documented thoroughly for the project.
 - As many conventions of its use followed in their recommended standard ways.
 - Any required licenses should be included as specified by the library.
 - Commercial code must be approved if necessary.

A team may decide to write wrapper code around the third party library and provide a more simple API for the code.

### React Best Practices

- Use functional stateless components when you don't need state in a component
- Do not use bind(). Declare all functions using ES6 arrow functions
- Never assign state a value in any other way except for using setState().
- Initialize your state objects with the most appropriate value.
- Keep immutability in mind.
- Always import the least amount of objects from a package/file as necessary.

#### Inclusion of Code

- Install Node.js and NPM
- Install create-react-app globally via NPM
- Initiate a new React app via create-react-app
- All production code must be built via npm/yarn build


Sample project directory

```markup
├── app/
│   ├── public/
|   |   ├── index.html
|   |   ├── manifest.json
|   |   ├── branding.ico
│   ├── src/
|   |   ├── components/
|   │   │   ├── App.js
|   │   │   ├── App.css
|   │   │   ├── Sidebar.js
|   │   │   ├── Sidebar.css
|   │   │   ├── ...
```

### Sources of Knowledge

- Go through the main concepts listed here in the official documentation before reading any other advanced topics
https://reactjs.org/docs/hello-world.html

- Connecting React and Redux
    https://react-redux.js.org/docs/introduction/quick-start

- Concepts of Redux
    https://redux.js.org/introduction/coreconcepts

- Debugging Redux -> Include redux-logger as middleware
    https://github.com/evgenyrodionov/redux-logger

- React Router -> Routes for a React SPA
    https://reacttraining.com/react-router/web/guides/quick-start
