# Restaurant SPA on React + Redux

A single-page restaurant application written in **React** and **Redux**, using asynchronous requests to an external **Json data base**.

## Contents

- [Restaurant single page on React + Redux](#restaurant-single-page-on-react--redux)
  - [Contents](#contents)
  - [Experience 🎓](#experience)
  - [Demo 🎥](#demo)
  - [How to Use 🔧](#how-to-use)
    - [Prerequisites 📋](#prerequisites)
    - [Running 🚀](#running)
  - [Features and structure 📓](#features-and-structure)
    - [Features](#features)
      - [React-Redux](#react-redux)
      - [Using React-Context and HOC](#using-react-context-and-hoc)
      - [Error Boundaries](#error-boundaries)
      - [JSON-Server](#json-server)
    - [Structure](#structure)

<h2 id="experience">Experience 🎓</h2>

In this project, I study and practice the following things:

- Redux
  - store > reducer > actions
  - dispatch
  - subscribe  
  - action-creators
- React+Redux
  - provider > connect > consumer
  - bindActionCreators
  - React Context
- HOC (Higher-Order Components)
- Error Boundaries
- Using JSON-Server

<h2 id="demo">Demo 🎥</h2>

The completed project can be viewed [here](https://rimerian.github.io/resto-spa/ "demo url")

<h2 id="how-to-use"> How to Use 🔧</h2>

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

<h3 id="prerequisites">Prerequisites 📋</h3>

You'll need [Git](https://git-scm.com) and [Node.js](https://nodejs.org/en/download/) (which comes with [NPM](http://npmjs.com)) installed on your computer.
Also, you can use [Yarn](https://yarnpkg.com/) instead of NPM ☝️

<h3 id="running">Running 🚀</h3>

From your command line, first clone "resto-spa":

```bash
# Clone this repository
$ git clone https://github.com/rimerian/resto-spa.git

# Go into the repository
$ cd resto-spa

# Remove current origin repository
$ git remote remove origin
```

Then you can install the dependencies either using NPM or Yarn:

Using NPM:

```bash
# Install dependencies
$ npm install

# Start development server
$ npm start
```

Using Yarn:

```bash
# Install dependencies
$ yarn

# Start development server
$ yarn start
```

**NOTE**:
If your run into issues installing the dependencies with NPM, use this command:

```bash
# Install dependencies with all permissions
$ sudo npm install --unsafe-perm=true --allow-root
```

Once your server has started, go to this url `http://localhost:3000/resto-spa` and you will see the website running on a Development Server:

![Web App started](/src/references/example.png)

<h2 id="features-and-structure">Features and structure 📓</h2>

### Features

#### React-Redux

The project uses the `redux` and `react-redux` libraries. 

**Redux** solves the problem of state management in the application by storing data in a **global state** and changing it centrally.

- **Components** formed by events (actions).
- **Reducer** — a logic module that handles listeners and changes state.
- Common **State** to all components.
- **Reducer + State = Store**.
- Components update when state changes .

#### Using React-Context and HOC

**React Context**, which is part of the main React library, provides our application a way to pass data through the component tree without having to pass props down manually at every level.

To reuse the component logic, a **higher-order component** (`with-resto-service.js`) is used in the project. It wraps the `resto-service` context binding logic and is exported for use in other components.

#### Error Boundaries

The project provides **Error Boundaries**(`error-boundary.js`) - React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. 
Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

#### JSON-Server

The data for the correct operation of the SPA is stored in JSON and processed in the `resto-service.js`.

To test the application locally, a [Json-server](https://www.npmjs.com/package/json-server) from the **npm** library was used.

The work of the project in the network is provided by the [service](https://my-json-server.typicode.com), which allows you to work with `db.json` hosted in the [github repository](https://github.com/rimerian/resto-spa-db.git)

### Structure

The project has a modular structure of the **React** application.
The "*kebab-case*" style is selected for naming the project files.
The main part of the application is located in the `src` directory.
The application is divided into `components`:

- `app`
- `app-header`
- `cart-table`
- `error`
- `eroor-boundary`
- `hoc`
- `menu-list`
- `menu-list-item`
- `pages`
  - `cart-page.js`
  - `item-page.js`
  - `main-page.js`
- `resto-service-context`
- `spinner`

Each component has, in addition to the main file, a style file in `scss` format and an `index.js` for convenience when exporting.

Receiving and Processing data from the JSON is assigned to the `resto-service.js` module in the `services` folder.

All components are assembled in the `app`, and then imported into the main `index.js` and there they are rendered to the web page (`index.html` inside `public` folder).

All app states are saved in the store (`store.js`).
The only way to change the state tree is to call action (`actions` folder), an object describing what happened.
The way in which actions transform the state tree is described by the `reducers`.