# MERN-Stack-TODO-Application
(FRONT END)


Part-1: Creating the backend

Initialized backend using npm and installed necessary dependencies
Set up MongoDB database
Set up a server using node.js and express.js
Created database schema to define a TODO
Created api routes to create, read, update and delete todo
In this part, we will
Set up our frontend using create-react-app
Create components for reading all the todo, creating todo and updating todo
Before getting started with Part-2
Store the contents of the part-1 in a folder named server and create a folder for client.

Part-2: Creating Frontend
1. Initializing our project
We'll initialize the create-react-app in the client folder. Run the following command from the terminal but make sure you are in the client folder.
npx create-react-app .
The . in the above command refers to the current folder. This will install our react app in the current folder instead of installing the app in a different folder.

2. Installing required dependencies
Within the client folder install the following dependencies
npm i node-sass axios react-router-dom
node-sass: allows using sass instead of css
axios: to make api calls to the backend
react-router-dom: for routing between pages
client's folders package.json should look something like in the above package.json.

3. Cleaning the src folder
Delete the logo.svg
Remove the imports from App.js
Remove the following from App.js

Delete the index.css file and remove the corresponding import from index.js

Rename the App.css file to App.scss and change the corresponding import at App.js
Run npm start. Open http://localhost:3000 and it should display Hello, World!

Copy and paste the styles from here and paste it in the App.scss file.

Now, we are good to start creating the frontend application.

4. Creating the components
.
├── node_modules
├── public
├── src <---------- we are here
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
Create a components folder inside the src folder and add the following files

createTodo.jsx
showTodoList.jsx
updateTodo.jsx
After adding these files, the folder structure will look something like this
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx
│   │   └── updateTodo.jsx
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
i. READ all the todo
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx <-- we are here
│   │   └── updateTodo.jsx
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
First, we will create the ShowTodoList component, to read all the documents that we created in the previous part while testing the backend application.

Import useState and useEffect hooks from react
Import axios from axios
In ShowTodoList function component will have a state todo, we will fetch the documents from the database and store it in the state todo.

We will use axios to send a GET request to the backend to fetch the document. Upon receiving the data we will store the data in todo using setTodo and log the data. If we receive an error we'll log that too.

We will make the get request from the useEffect hook, since we want the data to load when the page loads.

We will use the TodoCard component to display the contents of the todo. We will use map to iterate over todo and pass the contents to TodoCard which will display the contents of each todo document.

The contents of the showTodoList.jsx file should look something like this
We will import ShowTodoList component in the App.js file

The contents of the App.js file should look something like this
Now, start the server that we built in part-1
npm run dev
Now, start the client side application
npm start
Open http://localhost:3000 in your browser and it should display all the todo documents that was fetched from the database.

ii. CREATE a new todo
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx <-- we are here
│   │   ├── showTodoList.jsx
│   │   └── updateTodo.jsx
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
To create a new document we will send a POST request to our server using axios.

Import useState hook react
Import Link from react-router-dom
Define a function handleChange that will get the input data
Define a function handleSubmit that will send the POST request to the server
Declare data using useState hook with the following json
{
  "title": "",
  "description": ""
}
In handleChange method we will update the data when the input changes. We will call the setData() and declare a arrow function inside that will copy the contents of the previous data if any exists. In this e.target.name will be the name of the input element that will have either title or description.

In handleSubmit method,

Call e.preventDefault() to prevent the page from reloading when the submit button is clicked.
Send a POST request to the server with the data. If the data has been sent successfully to the server then reset the state data
After adding the above change the code will look something like this
iii. Update App.js
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx
│   │   └── updateTodo.jsx
│   ├── App.js <-------------- we are here
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
Before we can use the CreateTodo component we need to update App.js file.

Import BrowserRouter and Route from react-router-dom
Import CreateTodo component from components/createTodo
Create a Route for home page / and pass the ShowTodoList component
Create a Route for creating a new todo /create-todo
Wrap the Routes inside of the BrowserRouter
After making the changes the App.js file should look something like this
Since we have not added the button to navigate to http://localhost:3000/create-todo you can type this in your browser to check the CreateTodo component.

iv. Adding the Link to navigate to /create-todo to showTodoList.jsx
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx <-- we are here
│   │   └── updateTodo.jsx
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
Import Link from react-router-dom
Wrap a button inside of Link tag
After making the changes, the ShowTodoComponent will look something like this.
v. Creating the UpdateTodo component to send UPDATE request
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx
│   │   └── updateTodo.jsx <-- we are here
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
Import useState from react
Import axios from axios
The UpdateTodo component will have 3 props

_id
handleClose
handleEdited
The updateTodo.jsx file may look something like this.
vi. Adding the method to DELETE a todo
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx <-- we are here
│   │   └── updateTodo.jsx
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
We will make the following changes in showTodoList.jsx

Define a function handleDelete that will send a DELETE request to the server. This function will need the _id of the document to delete the document from the database. It will also update the array todo with the filtered array.
Pass the handleDelete method as a prop to TodoCard
Update TodoCard component to have the parameter handleDelete
Add an onClick event for the button delete and pass the handleDelete method
After making the changes, the code will look something like this
vii. Adding the UpdateTodo component in showTodoList.jsx
.
├── node_modules
├── public
├── src
│   ├── components
│   │   ├── createTodo.jsx
│   │   ├── showTodoList.jsx
│   │   └── updateTodo.jsx <-- we are here
│   ├── App.js
│   ├── App.scss
│   ├── App.test.js
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── .gitignore
├── package-lock.json
├── package.json
├── README.md
└── yarn.lock
We need to add the following changes in the showTodoList.jsx

Import UpdateTodo component from updateTodo.jsx
Declare open using the useState hook with the default value of false. The value of open will be either true or false. We will conditionally render the UpdateTodo component. If the edit button is clicked on any one of the todo then we will set open to true when the UpdateTodo component will be rendered.
Declare id using the useState hook. The _id of the todo document to be updated will be stored. It will be passed as a prop to UpdateTodo component.
Declare update using the useState hook. This will be used to fetch all the todo documents from the database. Each time a todo document has been updated then update will change between true and false
Define a function handleEdit. It will update the state id with the _id of the document and update the state of open to true. The UpdateTodo component will be rendered.
Define a function handleUpdate. This will invert the state of update if the todo has been updated by the user. Inverting the state will cause the useEffect hook to update the todo array.
Define a function handleClose. We need this to close the UpdateTodo component. This will set id to an empty string and set open to false.
Update the TodoCard component

Pass the handleEdit function to the TodoCard component.
Pass the handleEdit prop to the edit button.
After making the above changes, the code will look something like this
