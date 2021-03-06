## Tic Tac React

An implementation of the Tic-Tac-Toc game with React

+ Clone the repository or create the React app

+ Review the starting code

Starting code: https://codepen.io/gaearon/pen/oWWQNa?editors=0010

+ You can put the starting code in a single file for now!

### Step 1

+ Passing Data Through Props (Board -> Square)

Expected result:

![alt text](result_step1.png)

#### Solution:

In Board’s renderSquare method, change the code to pass a value prop to the Square.
Then change Square’s render method to show that value by replacing TODO with {this.props.value}:

![alt text](solution1.png)

Updated code:
https://codepen.io/gaearon/pen/aWWQOG?editors=0010


### Step 2

Let’s make the Square component fill in an “X” when you click it. Try changing the button tag returned in the render() function of the Square like this:

![alt text](step2.png)

Initialize the state:

![alt text](step2a.png)

Now change the Square render method to display the value from the current state, and to toggle it on click:

![alt text](step2b.png)

#### Debug it and see what's happening!!!

### Step 3

Add a constructor to the Board and set its initial state to contain an array with 9 nulls, corresponding to the 9 squares:

![alt text](step3.png)

We’ll fill it in later so that a board looks something like

![alt text](step3a.png)

Modify it to pass a value prop to Square.

![alt text](step3b.png)

This is the code now: https://codepen.io/gaearon/pen/gWWQPY?editors=0010

### Step 4

Now we need to change what happens when a square is clicked. The Board component now stores which squares are filled, which means we need some way for Square to update the state of Board. Since component state is considered private, we can’t update Board’s state directly from Square.

The usual pattern here is pass down a function from Board to Square that gets called when the square is clicked. Change renderSquare in Board again so that it reads:

![alt text](step3c.png)

Now we’re passing down two props from Board to Square: value and onClick. The latter is a function that Square can call. 

+ Let’s make the following changes to Square:

-> Replace this.state.value with this.props.value in Square’s render.

-> Replace this.setState() with this.props.onClick() in Square’s render.

-> Delete constructor definition from Square because it doesn’t have state anymore.

![alt text](step4.png)

BUT: Try clicking a square – you should get an error because we haven’t defined handleClick yet. 

-> Add it to the Board class.

![alt text](step4a.png)

Updated code: https://codepen.io/gaearon/pen/ybbQJX?editors=0010

### BONUS!

We’ve removed the constructor in Square and in fact, React supports a simpler syntax called functional components for component types like Square that only consist of a render method. Rather than define a class extending React.Component, simply write a function that takes props and returns what should be rendered.

![alt text](step4b.png)

### Step 5

At the moment in our game only X (or "player one") can play. Let’s fix that.

-> in Board class add a new state p.e. "xIsNext: true"

Each time we move we shall toggle xIsNext by flipping the boolean value and saving the state.

![alt text](step5.png)

Now X and O take turns. Next, change the “status” text in Board’s render so that it also displays who is next:

![alt text](step5b.png)

https://codepen.io/gaearon/pen/KmmrBy?editors=0010


### Step 6

How to declare the winner. We need a helper function for that

![alt text](step6.png)