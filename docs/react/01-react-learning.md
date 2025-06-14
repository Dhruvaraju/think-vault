# React Learning

To create a new react project run the following command:

```shell
npm create vite@latest <<PROJECT_NAME>> -- --template react
```

> Change the `<<PROJECT_NAME>>` to your desired name.

!!! Info "Starting app"

    Switch to the folder where the app is created.

    Run 
    ```
    npm install
    ```

    To start the app 
    ```
    npm run dev
    ```


## JSX

- Javascript as xml (jsx), by default react projects use jsx. 
- Javascript code and variables can be run as part of html.

**example:**

```jsx
let user = "admin";

return (
<h1>The role of user is {user}</h1>
<h6>Logged in as {user.toUpperCase()}</h6>
)

```

## Creating a component

- A new component can be created with a new function
- The function name will be used as the html tag.

```jsx
function Header(){
  return (
    <h1>Header component</h1>
  )
}

function App() {
  let user = "admin";

  return (
    <div>
    <Header></Header>
    <h1>User logged in as {user} </h1>
    </div>
  )
}

export default App
```

- In the above example Header function is embedded as a new component in app

## Passing properties to components

- Properties can be passed to a component in 2 ways
    - `props`.
    - destructuring `props`.

**Using props**

```jsx
function Header(props){
  return (
    <>
    <h1>Logged in User: {props.name}</h1>
    <h2>Role: {props.role}</h2>
    </>
  )
}

function App() {
  let user = "admin";

  return (
    <div>
    <Header name="dexter" role="admin"></Header>
    <h1>You are an {user} </h1>
    </div>
  )
}

export default App
```

**Using Destructuring**

```jsx
function Header({name, role}){
  return (
    <>
    <h1>Logged in User: {name}</h1>
    <h2>Role: {role}</h2>
    </>
  )
}

function App() {
  let user = "admin";

  return (
    <div>
    <Header name="dexter" role="admin"></Header>
    <h1>You are an {user} </h1>
    </div>
  )
}

export default App
```

## Working with lists

- We can add lists in the react components as below
- `possibleRoles` is the list that is being used.

```jsx
const possibleRoles = ["admin", "management", "developer", "devops"];

function AllRoles(props) {
  return (
    <ul>
      {props.roles.map((role) => (
        <li>{role}</li>
      ))}
    </ul>
  );
}

function App() {
  let user = "admin";

  return (
    <div>
      <Header name="dexter" role="admin"></Header>
      <h1>You are an {user} </h1>
      <AllRoles roles={possibleRoles}></AllRoles>
    </div>
  );
}

export default App;
```

!!! Note "Keys in Lists"

    React documentation suggests to use an unique key for each list item to keep track of changes.

### Using unique key for each list item

```jsx
const possibleRoles = ["admin", "management", "developer", "devops"];

const roleObjects = possibleRoles.map((role, i) => ({
  id: i,
  role: role,
}));

console.log(roleObjects);

function AllRoles(props) {
  return (
    <ul>
      {props.roles.map((role) => (
        <li key={role.id} style={{ listStyleType: "none" }}>
          {role.role}
        </li>
      ))}
    </ul>
  );
}

function App() {
  let user = "admin";

  return (
    <div>
      <Header name="dexter" role="admin"></Header>
      <h1>You are an {user} </h1>
      <AllRoles roles={roleObjects}></AllRoles>
    </div>
  );
}

export default App;
```

!!! Info "React Fragments"

    If a react component has more than one html element it need to be kept in a fragment.
    Generally a `<div>` can be used but it will add unnecessary div tag to dom.
    Instead `<React.fragment>` tag can be used or simply `<></>` can be used.
    Using `React.fragment` requires a react import where `<></>` does not need any import.