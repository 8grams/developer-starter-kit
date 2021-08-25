# JavaScript Front-end Development

This chapter purpose is to introduce developer to front-end development. As a result, since too many frameworks / libraries available, this chapter only discuss ReactJS (https://reactjs.org) which serves as library for Web user interface. It does not mean taht this library is the best, it is supposed to be an introduction so readers understand the component of fronot-end development in Web. We also do not discuss any other kind of front-end part such as terminal-based, GUI, and mobile.

## What is React?

__React__ (also called "ReactJS", "React.js") is library for building user interface developed by Facebook and currently maintained by Facebook, Instagram, and many parties. It is now in stable condition and future development will be focused on React Fibre.

## How React Works

React actually is a library for building user interface. Building interface does not merely related with layout but also how program flow and data changes affects UI. React uses declarative programming to describe UI.

As a UI library with huge features (and also support ES6), there are probably many things which need to be considered (including whether one has to use Redux for state management, etc), but in this sub chapter we will explain the basic building block of React app, other things might follow.

In React, the result will always be rendered to DOM (Document Object Model). DOM is a tree structure which represents HTML / XML "document". DOM provides API to enable developer in manipulating HTML / XML contents since it may be used to describe HTML / XML contents in a tree structure. HTML file is processed into DOM, the in-memory representation. Often, this DOM related manipulation is slow because of borwsers support and the need for I/O operation. React abtract DOM in virtual DOM, having them manipulated, and render the result into the DOM, this is why React has good performance.

In source code, React can be used to define element (which is stateless or immutable or static) and / or components which maintain its state. They are all declared with JSX, an extension of JavaScript for declarative code in building UI. React class is used to define component and in each component there are props (properties) for arbitrary inputs, maintain internal state, and return elements to DOM. Here is an example of React app (taken from official React website):

```
class TodoApp extends React.Component {
    constructor(props) {
        super(props);
        this.state = { items: [], text: '' };
        this.handleChange = this.handleChange.bind(this);
        this. handleSubmit = this.handleSubmit.bind(this);
    }
    
    render() {
        return (
            <div>
                <h3>TOD0</h3>
                <TodoList items={this.state. items} />
                <form onSubmit={this.handleSubmit}>
                    <label htmLFor="new-todo">
                        What needs to be done?
                    </label>
                    <input id="new-todo" onChange={this.handLeChange} value={this.state.text} />
                    <button>Add #{this.state.items.length + 1}</button>
                </form>
            </div>
        )
    }
    
    handleChange(e) {
        this.setState({ text: e.target.value });
    }
    
    handleSubmit(e) {
        e.preventDefault();
        if (!this.state.text.length) {
            return;
        }
        
        const newltem = {
            text: this.state.text,
            id: Date.now()
        };
        
        this.setState(prevState => ({
            items: prevState.items.concat(newItem),
            text: '' 
        }));
    }
}

class TodoList extends React.Component {
    render() {
        return (
            <ul>
            {this.props.items.map(item => (
                <li key={item. id}>{item. text}</li>
                ))}
            </ul>
        );
    }
}

ReactDOM.render(<TodoApp />, mountNode);
```

## Getting Started with React

Basically, developer may use React for new application or add React to existing application. For existing application, there is a web page dedicated to ease developer in using React for existing application: https://reactjs.org/docs/add-react-to-an-existing-app.html. For new application, there is a package which should be installed first: create-react-app:

    ~$ npm install -g create-react-app

Use create-react-app to create a skeleton of new React app:

create-react-app first-react-app

```
Creating a new React app in

/home/8grams/projects/first-react-app.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts...

yarn add v1.5.1
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
info fsevents@1.1.3: The platform "Linux" is incompatible with this module.
info "fsevents@1.1.3" is an optional dependency and failed compatibility check.
Excluding it from installation.
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 743 new dependencies.
info Direct dependencies
-- react-dom@16.2.0
-- react-scripts@1.1.1
-- react@16.2.0

info All dependencies
-- ababal.@.4
...
...
...
-- xtend@4.0.1
-- yallist@2.1.2
-- vargs-parser@5.0.0

Done in 204.79s.

Success! Created first-react-app at
/home/projects/first-react-app
Inside that directory, you can run several commands:

    yarn start
        Starts the development server.
        
    yarn build
        Bundles the app into static files for production.
        
    yarn test
        Starts the test runner.
        
    yarn eject
        Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

    ~$ cd first-react-app
    ~$ yarn start

Happy hacking!
```

Just to have a taste of how React application runs, run it using yarn start:

```
yarn start
yarn run v1.5.1
~$ react-scripts start

Compiled successfully!
You can now view first-react-app in the browser.
    Local:              http://localhost:3000/
    On Your Network:    http://192.168.1.3:3000/

Note that the development build is not optimized.
To create a production build, use yarn build.
```

Source code exist in __src/__ directory. The displayed web page is in __src/App.js__ which can be edited to suit the problem that developer wants to solve.

To get started in using IDE to build React based application, use these:

- Reactide, an IDE for React: https://reactide.io
- React plugin for Atom editor: https://orktes.github.io/atom-react/

Some components has been built by communities:
- Bootstrap 3 components built with React: https://github.com/react-bootstrap/react-bootstrap
- Simple React Bootstrap 4 components: https://github.com/reactstrap/reactstrap
- React components that implement Google’s Material Design: hittps://github.com/mui-org/material-ui
- A flexible and beautiful UI framework for React.js: https://github.com/elementalui/elemental
- Some components from for Khan Academy: https://github.com/Khan/react-components

React Architecture:
- Redux: https://redux.js.org
- Flux: http://facebook.github.io/flux