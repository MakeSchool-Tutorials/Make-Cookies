---
title: "Cookie Manufacturing Facility!"
slug: Cookie-Manufacturing-Facility
---

We are now on our last **user story**! Don't get too ahead of yourself though, because once we have all **user stories** completed we'll need to check for **balance**, and improve pieces of code wherever we can.

The goal of developing all of our user stories is to create a **minium viable product**. Once this is complete we get to focus on the things that really make a **user experience** better.

We will recall our final user story:

- As a user, I can purchase Cookie Manufacutring Facilities that increase my number of cookies automatically.

# Adding the markup
Just like all cookies need ingredients, we will put our ingredients into our HTML to make our cookie manufacturing facility. Put this right beneath the grandma markup.

```HTML
<!--Cookie Manufacturing Facility-->
<hr>
<p>Cookie Manufacturing Facility</p>
<p>Producing <span id="facility-multiple">0</span> cookies per second!</p>
<button id="buy-facility">Buy for <span id="facility-price">100000</span></button>
<p>Level: <span id="facility-level">0</span></p>
```

Great. Now we are ready to add some functionality to our facilities!

# Adding functionality to our facilities
Let's just jump right into it. We've done most of this with the other modules, and functionality wise, our facility will be the same as our grandmas, but more efficient.

Let's start again by defining a *function* and listing all of our steps inside of our ```scripts.js``` file:

```js
/********************************

          Facilities

********************************/

//set default values

//declare DOM variables

//buy a facility

//game loop

//refresh shop


```
We will put all of our code inside those comments.

Let's declare our variables now:

```js
//set default variables
let facilityAuto = false;
let facilityPower = 2000;
let facilityPriceAmount = 100000;
let facilityLevelNumber = 0;

//declare DOM variables
let buyFacility = document.getElementById('buy-facility');
let facilityPrice = document.getElementById('facility-price');
let facilityLevel = document.getElementById('facility-level');
let facilityMultiple = document.getElementById('facility-multiple');

```

Woohoo. Now we can start our buy facility function. Let's make sure to get all the steps in first.

```js
//buy a facility
buyFacility.addEventListener("click", function() {
    //set autoLoop to false
    facilityAuto = false;

    //make sure we have enough cookies

    //upgrade power level

    //update price

    //update facility power

    //turn autoFacility on!

    //refresh shop item

  }
})

```
Now all we have to do is go through and add in the code.

```js
//make sure we have enough cookies
if (cookieCount >= facilityPriceAmount) {
  cookieCount -= facilityPriceAmount;
  refreshCookieCount()

  //upgrade power level

  //update price

  //update facility power

  //turn autoFacility on!

  //refresh shop item

    }//DONT FORGET THIS BRACKET
  }
})

```

Perfect. Now we can purchase a facility. Let's add all the other bits now:

```js
//upgrade power level
facilityLevelNumber += 1;

//update price
facilityPriceAmount = Math.floor(facilityPriceAmount * 1.33);

//update facility power
facilityPower += 600;

//turn autoFacility on!
autoFacility = true
autoFacilityStart();

//refresh shop item
refreshFacility();

```
Great. To finish this up we need to add two in the two functions below. We will start with our ```refreshFacility``` function.

```js
//refresh shop
let refreshFacility = function() {
  facilityLevel.innerHTML = facilityLevelNumber
  facilityPrice.innerHTML = facilityPriceAmount;
  facilityMultiple.innerHTML = facilityPower - 600;
}
```
Remember that we subtract 600 so that at level 1, we have our set default amount.

It's time to set up our game loop:

```js
//game loop
let autoFacilityStart = function() {
    let facilityInt = window.setInterval(function(){
      cookieCount += facilityPower;
      refreshCookieCount();
    }, 1000);
}
```

And that should do it! We now have a minium viable product for our game. But... something isn't quite right. At a certain point, leveling up past a certain point doesn't seem to be worth the price.

# Onward
In the next session we will adapt some balance fixes for end-game users.
