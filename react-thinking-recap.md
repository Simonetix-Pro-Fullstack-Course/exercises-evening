## Instructions
### Iteration 0 | Introduction 

In the `src/` folder, you will find the `data.json` file containing the data representing products of a random store.

Each product object has the following fields: `category`, `price`, `inStock` and `name`, of which `inStock` is type _boolean_ (this information will be valuable soon). Example:

```json
{
    "category": "Sporting Goods",
    "price": "$49.99",
    "inStock": true,
    "name": "Football"
}
```


You will be dealing with multiple components that depend on each other. To properly reflect the changes in all the components, we'll store the state in the closest common parent component (remember _lift the state up_).

You will be dealing with multiple components that depend on each other. To ensure that components can interact with each other, we'll store the state in the closest common parent component (remember _lifting the state up_).

And remember, this is just an exercise and a part of the learning process. No one expects you to do it perfectly. Think it through, ask questions, be curious and explore all possibilities. Let's do this! :wink:



----



### Iteration 1 | Break The UI Into A Component Hierarchy

So remember: the proper planning will save you a lot of time when building the app. The first thing you’ll want to do is to make a sketch on the piece of paper: draw boxes around every component (and sub-component) and give each component a name.
A possible approach could be something like this:

<!-- ![image](https://user-images.githubusercontent.com/23629340/42808309-54d1594a-89b3-11e8-9df3-450127e4459e.png) -->

<details>
  <summary>Click here to see the image</summary>


  <hr>


![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-thinking-in-react/thinking-in-react-1.png)

</details>

As you can see here, we have four components in our app:

- **ProductsPage (orange):** contains the entirety of the example (we will render it in the `App.js`)
- **SearchBar (blue):** having an input that takes the user's search string
- **ProductTable (green):** displays all the products and also shows the filtered products based on the user's search
- **ProductRow (red):** displays a row (_table data_) for each product

Now that we’ve identified the components in our app let’s arrange them into a hierarchy. Components that appear within another component should appear as children in the hierarchy:

- ProductsPage
  - SearchBar
  - ProductTable
    - ProductRow



----



### Iteration 2 | Products Page

First, let's create a `components/` folder and our first component `ProductsPage.js`. This component will be the _parent_ of the other components.

We'll give you a starter hint to kick off the project: this component should have a state variable holding the array of products. It should then pass down the products to other components that need them. So to start, you should import the `data.json` file and create a state variable in the following way:

```jsx
// src/components/ProductsPage.js

import { useState } from 'react';
import jsonData from './../../data.json';

function ProductsPage () {
  const [products, setProducts] = useState(jsonData);
  
  return(
      <div>
        <h1>IronStore</h1>
      </div>    
  )
}
```



Next, let's import and render the `ProductsPage` component in the `App.js`:

```jsx
// App.js
import './App.css';
import ProductsPage from './components/ProductsPage';


function App() {
  return (
    <div className="App">
      <ProductsPage />
    </div>
  );
}

export default App;
```



Okay, now it's your turn. Create the `<SearchBar />` and the `<ProductTable />` components to display the search bar and the list of products. You should render both components inside the `ProductsPage` (see the sketch above 😉).


----


### Iteration 3 | Product Row

Next, create a `<ProductRow />` component and use it to display each product in the list. This component should be rendered inside of the `ProductTable`. 

The products that are out of stock should be colored in **red**. _Hint:_ Each product object has a property `inStock` which you can use to change the text color conditionally.

<details>
  <summary>Click here to see the image</summary>


  <hr>


![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-thinking-in-react/thinking-in-react-4.png)

</details>

<!-- ![image](https://user-images.githubusercontent.com/23629340/42808421-95a78a66-89b3-11e8-85c1-3246127a7f1a.png) -->



----



### Iteration 4 | Filter the Products

In this iteration, we'll add the list filtering functionality. Every time someone types a letter in the search input, the list should update based on the user's input.
_Hint:_  Search functionality can be easily implemented using an `input` with the `onChange` handler, which will update the state on every keystroke.

<details>
  <summary>Click here to see the image</summary>



  <hr>



![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/lab-thinking-in-react/thinking-in-react-2.gif)

</details>



----
