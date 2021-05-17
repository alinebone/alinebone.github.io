---
layout: post
title: Create Vanilla JS list pagination
categories: development english
---

Some time ago I was in a situation where I needed to create a snippet containing a list that should display four items at a time. I wanted to use pure JavaScript as in my mind it would be as easy as pie.  
However, I ended up taking more time to do it than I thought. So here I am perpetuating this to never forget it. 😅  

[Jump into the code!]()

# Part 1 - Wrapping up the base

  - Create the project folder containing 2 items: `index.html` and `script.js`.

  - Right above the end of the `body` tag, add the `script.js` file:
  ```html
  <script src="script.js"></script>
  ````

# Part 2 - HTML structure

  - In the `index.html` add the wrapper to hold the list:
  ```html
  <ul id="favorite-fruits">
  </ul>
  ```

  - Also, create the wrapper to hold the pagination items.
  ```html
  <nav id="pagination">
  </nav>
  ```

  To keep a good **semantic HTML** structure. Let's create a `header` element to keep our title, and a `main` element to hold our list of items.    

  *The pagination wrapper is a `nav` inside `main` because it relates direct to the main content*

  The final result for the `index.html` will be:
  ```html 
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Vanilla JS Pagination</title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <header>
      <h1>My favorite fruits</h1>
    </header>
    <main>
      <ul id="favorite-fruits">
      </ul>
    </main>
    <script src="script.js"></script>
  </body>
  </html>
  ``` 

# Part 3 - Displaying a list of items

Now we start to build the `javascript` file.

- In the `script.js` Create an `array` of your favorite fruits:
 
```javascript
const fruits = ["Watermelon", "Strawberry", "Avocado", "Banana", "Cherries", "Lime", "Mango", "Nectarine", "Pear", "Pitaya", "Pitanga", "Mandarin", "Lemon", "Coconut"];
```

- Get the list container:

```javascript
const fruits_element = document.getElementById('favorite-fruits');
```

- Create a function to display the fruits:

```javascript
displayFruits = () => {
  for (let i = 0; i < fruits.length; i++) {
    var li = document.createElement("li");
    li.innerHTML = fruits[i];
    fruits_element.appendChild(li)
  }
}
```

- Call the function at the end of the `javascript` file. 

```javascript
displayFruits();
```

# Part 4 - Loading only the current page

- Setup the variables to hold the current page, the number of items per page, and the number of pages.

```javascript
let current_page = 1;
let items_per_page = 4;
let number_of_pages = Math.ceil(fruits.length / items_per_page);
```

- Change the `displayFruits()` method to show only the current page. 

```javascript
displayFruits = (page) => {
  fruits_element.innerHTML = "";
	page--;

	let start = items_per_page * page;
	let end = start + items_per_page;
	let paginatedItems = fruits.slice(start, end);

	for (let i = 0; i < paginatedItems.length; i++) {
		let item = paginatedItems[i];

		let item_element = document.createElement('div');
		item_element.innerText = item;
		
		fruits_element.appendChild(item_element);
	}
}
```

- Call the function at the end of the `javascript` file passing the `current_page` as a parameter. 

```javascript
displayFruits(current_page);
```

# Part 5 - Show pagination buttons

- Get the pagination wrapper

```javascript
const pagination_element = document.getElementById('pagination');
```

- Create the `addPagination()` method and calculate the number of pages we need based on the length of the fruit list and the `items_per_page` we defined in the previous step.

```javascript
addPagination = () => {
  let number_of_pages = Math.ceil(fruits.length / items_per_page);
}
```

- Add the button event listener to change the page.
```javascript
addPagination = () => {
  for (let i = 1; i < number_of_pages + 1; i++) {
    let button_element = document.createElement('button');
    button_element.innerText = i;

    button_element.addEventListener('click', function () {
      current_page = i;
      displayFruits(i);
    });

    pagination_element.appendChild(button_element);
	}
}
```

- Call the function `addPagination()` in the end of the `javascript` file. 

```javascript
addPagination();
```

- Inside the `addPagination()` function, add a iteration to create and load the pagination buttons. Start the index with one as our pages start from 1, and create the `button` element.

```javascript
  for (let i = 1; i < number_of_pages + 1; i++) {
    let button_element = document.createElement('button');
	}
```

- To display the buttons correctly, add the index `i` as the text of the buttons, and append the element to the `pagination_element`

```javascript
  for (let i = 1; i < number_of_pages + 1; i++) {
    let button_element = document.createElement('button');
    button_element.innerText = i;
    pagination_element.appendChild(button_element);
	}
```


