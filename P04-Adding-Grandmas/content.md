---
title: "Adding Grandmas!"
slug: Adding-Grandmas
---

We are now on our third user story:

- As a user, I can purchase Grandmas that increase my number of cookies automatically.

Every time a user buys a grandma, they will start to earn cookies without doing anything. Grandma's got you covered.

# Adding the markup

The first thing we need to do is put some **elements** on our page to *interact with*, and **assign them ID's** that we can target with JavaScript.

Let's add the following ```HTML``` underneath the previous shop item.

```HTML
<!---GRANDMAS-->
<hr>
<p>Grandmas</p>
<p>Producing <span id="grandma-multiple">0</span> cookies per second!</p>
<button id="buy-grandma">Buy for <span id="grandma-price">500</span></button>
<p>Level: <span id="grandma-level">0</span></p>

```

Now we can start to add functionality to these.

# Declaring our variables
First we will create a new section inside of our ```scripts.js```

Let's add the following at the bottom of our file:

```js


/********************************

          Grandmas

********************************/

```

And now we will declare the following **default variables**:

```js
//set default values
let grandmaPower = 50;
let grandmaPriceAmount = 500;
let grandmaLevelNumber = 0;

//declare DOM variables
let buyGrandma = document.getElementById('buy-grandma');
let grandmaPrice = document.getElementById('grandma-price');
let grandmaLevel = document.getElementById('grandma-level');
let grandmaMultiple = document.getElementById('grandma-multiple');
```
Feel free to change the values of ```grandmaPower``` and ```grandmaPriceAmount``` as you wish. This is *your* game.

# Adding our on click function
Now that we've declared our *variables* we can start creating the *function* that occurs once we click the buy button.

This function will be largely similar to the previous one, the only difference is that we will be setting a **game loop** that increases our cookie amount every second.

So lets get started by writing the following lines of code:

```js
//buy a grandma
buyGrandma.addEventListener("click", function() {

})

```
Because we are master coders that make plans before coding, let's add the steps we need to take first! Inside of this function, let's add the following:

```js
buyGrandma.addEventListener("click", function() {

  //make sure we have enough cookies and subtract our cookies from the price

  //upgrade power level

  //update price

  //update grandma power

  //turn autoGrandma on!

  //refresh shop item

})
```

Now we can tackle each step *one at a time*, starting with the first.

To make sure we have enough cookies, we need to *compare* our cookies with the price of the grandma, and then **subtract** our total cookies by the **same** price.

We can do that with this block of code:

```js
 // Make sure we have enough cookies and subtract our cookies from the price.
 if (cookieCount >= grandmaPriceAmount) {
   // Subtract cookies from the price of the item.
   cookieCount +=  - grandmaPriceAmount;
   refreshCookieCount()

   // Upgrade power level.

   // Update price.

   ...
 }
```

Now the button has some basic functionality, but let's add all the other stuff!

# Adding the other stuff!
Just like once you can get the hang of baking cookies, we are getting the hang of adding things to our *functions*. In our case, all we have to do is change our variable names.

So let's complete our other code blocks one at a time, with this in mind.

Here's how we can upgrade our grandma's power level:

```js

//upgrade power level
grandmaLevelNumber += 1;

```

Now we will update the price:

```js
//update price
grandmaPriceAmount = Math.floor(grandmaPriceAmount * 1.33);

```

Next we can upgrade our grandmas power. This is the amount of cookies we want to our grandma to produce every level up. Let's do 10 for each level to start.

```js
//update grandma power
grandmaPower += 10;

```

We will skip over the game loop until after we add the refreshGrandma function.

```js
//turn autoGrandma on!

//refresh shop item
refreshGrandma();

```
Now we have to create the ```refreshGrandma()``` **function**. Let's do it below our **event listener** function.

# Refresh Grandma!

Let's add the following *function*:

```js
let refreshGrandma = function() {
  grandmaLevel.innerHTML = grandmaLevelNumber
  grandmaPrice.innerHTML = grandmaPriceAmount;
  grandmaMultiple.innerHTML = grandmaPower;
}

```

# Our first game loop!
Now is the moment we've been waiting for. This is what seperates a bad cookie from a good cookie, and we all know that grandma's make the best cookies.

Let's first set a **default variable** to the **boolean** *False*, and when it becomes *true*, our **game loop** will run.

At the top of our Grandma section lets add the following:

```js
//set default values
let grandmaAuto = false;
```

Now inside of our buy grandma code block, let's add the following code:

```js
//turn autoGrandma on!
autoGrandma = true
autoGrandmaStart();

```

We declare the **boolean** *true*, and then run the ```autoGrandmaStart()``` function which we will create above the refresh grandma function.

So let's set up our game loop. We will do this with the ```window.setInterval()``` function.

Here's an example of how it looks:

```js

window.setInterval(function(){
  //executing code loop goes here
}, numberOfMilliSeconds)

```

Now we can create our **game loop**! Lets use the following code:

```js
let autoGrandmaStart = function() {
  let grandmaInt = window.setInterval(function(){
    cookieCount += grandmaPower;
    refreshCookieCount();
  }, 1000);
}

```
If we test our code by using our app in the browser and buying a grandma, we will see something unexpected.

Instead of increasing by our set amount of 50, we get 60 because in our code block we decided to add 10 for each level.

So let's make sure that the first level stays at 50 by implementing the following line of code inside our 

`refreshGrandma()`

function:

```js
let refreshGrandma = function() {
  ...
  grandmaMultiple.innerHTML = grandmaPower - 10;
}

```

Now it should work as expected.

# Onward!

We've done it. We have our first game loop.

In the next section we will add another game loop.
