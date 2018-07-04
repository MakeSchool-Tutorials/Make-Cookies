In the last section we got our first shop item working. In this section we will be making it easier to add new code by seperating everything into seperate files.

# Moving to .js files
To start, from the terminal, enter the following command:

```
touch scripts.js
```

Once you've got a scripts file we need to link up to it in our HTML.

Above our current ```<script>``` tag lets put in the following HTML.

```
<script src="./scripts.js"></script>
```
Then we can cut everything in between the other script tags, and paste it into our new ```scripts.js``` file.

# Seperating our code with comments
First, let's make sure everything is still working correctly by testing our webpage out. Once we have confirmed that everything is still working we will divide our code into different sections.

Right now we should only have two sections, one for our main cookie clicker, and one for our power click.

First we will start at the top of our ```scripts.js``` file and write the following:

```js
/********************************

        COOKIE clicker

********************************/
```

Underneath ths, we will add everything that isn't for power clicking.

We should get something similar to this:

```js
//defaults
let cookieCount = 0;

//DOM decleration
let cookieCounter = document.getElementById('cookie-counter');
let cookieClicker = document.getElementById('cookie-clicker');


//everytime a user clicks the button, their cookies are increased by the value of their clickPower.
cookieClicker.addEventListener("click", function() {
  cookieCount = cookieCount + clickPower;
  refreshCookieCount()
})

//refresh cookies
let refreshCookieCount = function() {
  cookieCounter.innerHTML = cookieCount;
}

```
Next we will do the same for the powerclick code. Below our refresh cookies function, lets add in another comment:

```js

/********************************

        Click Power

********************************/


```

And then finally we will make sure to move our code blocks for all of our click power variables, and functions underneath this comment.

Don't forget to add seperate comments to show things like ```//default variables``` and ```declare DOM variables```.

# Onward

Now that we have organized our code a little better, it will be easier to read, and adding in new blocks of code will make more sense. In the next step, we will be adding in our first game loop, and another shop item.
