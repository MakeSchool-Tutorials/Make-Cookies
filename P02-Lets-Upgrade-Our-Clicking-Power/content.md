---
title: "Lets upgrade our clicking POWER!"
slug: Lets-Upgrade-Our-Clicking-Power
---
We can increase our cookie count, but there's *no goal* for our players to strive for. We need to *develop positive incentives* to encourage our users to continue clicking our Make Cookies button.

# Creating a shop
We want our players to be able to trade in their cookies for various different upgrades.

To start we will create a section for our upgrades to live in.

Below our last ```<button>``` **element** will add the following ```HTML```:

```html
<hr>
<h2>Shop</h2>
<hr>
```
Lets consider for a moment everything we will need.

We need **markup** that allows players to purchase new upgrades, level them up, keep track of how many times they have leveled up that specific upgrade, and how much many cookies they can produce.

Let's add the following ```HTML``` to keep track of all that stuff.

```html
<p>Click Power</p>
<p>Produces <span id="click-power-multiple">1</span> cookie(s) per click</p>
<button id="buy-click-power">Buy for <span id="click-power-price">50</span></button>
<p>level: <span id="click-power-level">1</span></p>
```
Because we want to change some of the content inside of our **HTML**, we put in ```<span>``` tags with **ID's** that we can traget. We set up the **default values** inside of our HTML that we want them to have. In this case, we will be able to level up click power for 50 cookies, and we start off with a click power of 1.

Everytime we level up our Clicking Power, we want to increase the effectivness of each of our clicks by **1**, and adjust the price so it's a little bit higher.

# Track our new HTML
Inside of our ```<script>``` *element*, let's create a new **variable** under our other **efault variables** that will be used to keep track of our cookie power level.

```js
//default variables
let clickPowerPriceAmount = 50;
let clickPowerLevelNumber = 1;
```

And now we will *declare variables that target our unique ID's* in the **DOM**.

```js
//declare DOM variables
let buyClickPower = document.getElementById('buy-click-power');
let clickPowerPrice = document.getElementById('click-power-price');
let clickPowerLevel = document.getElementById('click-power-level');
let clickPowerMultiple = document.getElementById('click-power-multiple');
```

We are now ready to make this shop work!

# Making our shop work!
When we hit the *buy click power* button, we need to do the following things.

- Make sure we have enough cookies to buy that item.
- Take away cookies based on the price.
- Update our Click Power level
- Increase the price for the next level
- Increase our click power.
- Update how much cookies we are producing.

We will do them in order, starting with the first.

Lets add a new **event listener** at the bottom of our ```script``` tag.

```js
//Buy click power
buyClickPower.addEventListener("click", function() {
  if (cookieCount >= clickPowerPriceAmount) {
    console.log("Item succesfully Bought");
  } else {
    console.log("You don't have enough cookies!");
  }
})

```
Now let's check our our page, hit the button, and watch what happens inside of our **developer console**. If we have enough cookies then we should get the first ```console.log``` statement. Otherwise we should get the latter.

Next we can add a line of **JavaScript** to take away cookies based on the price.

```js
if (cookieCount >= clickPowerPriceAmount) {
  //subtract cookies from the price of the item
  cookieCount +=  -clickPowerPriceAmount;
  //update cookie counter.
  cookieCounter.innerHTML = cookieCount;
}  
 ...

```

We will need to use ```cookieCounter.innerHTML = cookieCount``` constantly throughout this project. So let's just turn it into a **function** that we can easily understand.

At the bottom of the ```<script>``` element lets add the following lines of code:

```js
let refreshCookieCount = function() {
  cookieCounter.innerHTML = cookieCount;
}
```

Now we can **refactor** several blocks of code to use that **function** instead:

```js
//everytime a user clicks the button, their cookies are increased by the value of their clickPower.
cookieClicker.addEventListener("click", function() {
  cookieCount = cookieCount + clickPower;
  refreshCookieCount()
})
```

```js
if (cookieCount >= clickPowerPriceAmount) {
  //subtract cookies from the price of the item
  cookieCount +=  -clickPowerPriceAmount;
  refreshCookieCount()
}
```

Great! Now we need to update our click power level. Let's create a **function** to refresh this shop item at the bottom of the ```<script>``` tag.

```js
let refreshPowerClick = function() {
  clickPowerLevel.innterHTML = clickPowerLevelNumber;
}

```

Now we can add these lines to our buy function:

```js

if (cookieCount >= clickPowerPriceAmount) {
  //subtract cookies from the price of the item
  cookieCount +=  -clickPowerPriceAmount;
  refreshCookieCount()

  //Upgrade power level
  clickPowerLevelNumber += 1;

  //refresh shop item
  refreshPowerClick();

}
```

We need to increase the price each time we level up.

There are a few ways that we could implement this.

- We could set up prices based on each level, and do so manualy. (Eg: level 1: 50, level 2: 100)
- We could make it go up by a certain amount each level.

We are going to do the second one so users can upgrade their clickPower to infinity! (and BEYOND!?)

```js

//Upgrade power level
clickPowerLevelNumber += 1;

//Update click price
clickPowerPriceAmount = Math.floor(clickPowerPriceAmount * 1.33);

//refresh shop item
refreshPowerClick();


```

Lets then add another line to our ```refreshPowerClick()``` function.

```js
let refreshPowerClick = function() {
  clickPowerLevel.innerHTML = clickPowerLevelNumber;
  clickPowerPrice.innerHTML = clickPowerPriceAmount;
}
```

Finally, we can update our clickPower so we actually get more cookies per click.

```js
//Update click price
clickPowerPrice = Math.floor(clickPowerPrice * 1.33);

//update Click Power
clickPower += 1;

//refresh shop item
refreshPowerClick();
```

Now all that's left to do is update our ```refreshPowerClick()``` function and we've got a working shop item.

```js
let refreshPowerClick = function() {
  clickPowerLevel.innerHTML = clickPowerLevelNumber
  clickPowerPrice.innerHTML = clickPowerPriceAmount;
  clickPowerMultiple.innerHTML = clickPower;
}
```
# Onward
Woohoo! That's a lot of stuff to keep track of!

In the next part we will **refactor** some of our code to make it easier to edit, update, and read. Now is also a great time to test that your shop is working as expected.
