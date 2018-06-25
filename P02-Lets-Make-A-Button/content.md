---
title: "Lets Make A Button!"
slug: make-a-button
---


In the last step we created an element that will display how many cookies we have and a button with no functionality.

In this part of the tutorial we will be getting that button to work!

# Adding ID's to elements

In order to interact with the DOM in Javascript, we first need to give the elements we want to interact with unique ID's that we can target in javascript.

Inside of index.html, let's locate our ```<h1>``` and ```<button>``` elements.

```
<h1>0</h1>
<button>Make Cookies</button>
```

We will append unique ID's to these elements like this:

```
<h1 id="cookieCounter">0</h1>
<button id="cookieClicker">Make Cookies</button>
```

Great. Next we will add a bit of Javascript to track our cookies.

# Tracking our cookies!

Inside of index.html, right before the closing ```body``` tag, we will add in a ```script``` tag.

This is where we will put our Javascript code for now.

```
...

  <script>

  </script>
</body>
```

Once we've done that we're ready to start coding some basic javascript.

The first thing we should do is set the default value of our cookie count to a variable.

In this case, our default value is 0, because we start off with 0 cookies.

Inside of the ```script``` tag, let's add the following lines of code:

```
//declare default variables
let cookieCount = 0;
```

Now we need to set the value of our ```<h1>``` tag to be equal to the value of our ```cookieCount``` variable.

We will do this first, by assigning a variable for that specific h1 tag, and then setting it's inner HTML equal to our ```cookieCount```.

```
<script>
  //set default values
  let cookieCount = 0;

  //declare DOM variables
  let cookieCounter = document.getElementById('cookieCounter');

  cookieCounter.innerHTML = cookieCount;
</script>

```

We can test if this works by changing the value of ```cookieCount``` from 0, to another number, refreshing our page, and looking for a change. Give it a try before moving on.

# Make Some Cookies!

Now that we are tracking our cookieCount, we can make clicking the button increment the amount of cookies we have by 1.

First, we should create a variable that sets how many cookies will be created per click, and a variable that selects the element.

```
  ...

  //set default values
  let cookieCount = 0;
  let clickPower = 1;

  //declare DOM variables
  let cookieCounter = document.getElementById('cookieCounter');
  let cookieClicker = document.getElementById('cookieClicker');

  ...
</script>

```

Now we can add an event listener that executes some code every time a user clicks on the button.

Add the following lines of code right before the closing ```<script>``` tag.

```
...

  //everytime a user clicks the button, their cookies are increased by the value of their clickPower.
  cookieClicker.addEventListener("click", function() {
    cookieCount = cookieCount + clickPower;
    cookieCounter.innerHTML = cookieCount;
  })

</script>
```

If we click our button on the webpage, we should see our number increment by 1. Feel free to change the value of clickPower to a larger number to go up more than one.

# Onward

We now have a very simple cookie clicker. It isn't very fun yet though, and players don't have much of an objective.
In the next section we will add a way to increase our clickPower!
