# The Deal With Functions

We know about variables in JavaScript, right? You tell JavaScript a name, and it remembers that the name equals a certain value, which can be any datatype.

```javascript
let myAwesomeVar = "cool string"
let mySecondVar = [3, "wow", "9"]
```

Awesome. JS can remember names!

## Naming functions

We can also give a name to a block of code. This is called a *function*. The most straightforward way to name it is this:

```javascript
function myAwesomeFunction () {
    // this is where the block of code goes
    // everything we write between { and } is now called "myAwesomefunction" 
    // -- JS will remember this name!
}
```

We can put *whatever we want* between the curly braces -- any set of instructions that work in JavaScript, we can stick 'em in there. Like this:

```javascript
function anotherFunction () {
    let x = 666
    let y = "420"
    console.log(x, y)
}
```

JS will remember that those three lines between the curly braces are called "anotherFunction". But it won't actually *run* them until we ask it to. We do that by *invoking* the function, like this:

```javascript
anotherFunction()
```

We can invoke it as many times as we want. Any time we want those lines to run, we just tell JS to do it:

```javascript
anotherFunction()
anotherFunction()
anotherFunction()
anotherFunction()
```

Just say the magic word, and JavaScript runs the lines you described.

## Parameters

We can also pass information into a function from *outside* using a parameter. Parameters get names, too:

```javascript
function myParamFunction(myCoolParamName) {
    // some code to run!
}
```

Setting a parameter name tells JavaScript: "Whatever gets passed in here, give it this name!" Then *within these curly braces*, that name equals whatever gets passed in when the function is *invoked*. Check this out:

```javascript
function gettingTheParam(xxx) {
    // the above is like saying "WHATEVER they put in here, call it 'xxx'"
    console.log(xxx)
}

gettingTheParam('hi there')
// xxx = 'hi there'

getttingTheParam(999)
// xxx = 999

gettingTheParam([3,6,12])
// xxx = [3,6,12]
```

Above, we simply logged `xxx` to the console. But we can do *anything with that value that we want to* -- within these two curly braces, we've got unrestricted access to `xxx`. This function checks to see if `xxx` is a string or a number or neither, then does string stuff or number stuff to `xxx` if it can:

```javascript
function gettingTheParam(xxx) {
    // checks to see if xxx is a string!
    if (xxx.toString() === xxx) {
        console.log(`It's a string that reads ${xxx}.`)

    // otherwise checks to see if xxx is a number!
    } else if (Number(xxx) === xxx) {
        // does some math!
        const lots = xxx * xxx * xxx
        const little = xxx - 666
        console.log(lots, little)
    } else {
        console.log(`${xxx} is neither string nor number.`)
    }
}
```

`xxx` will be equal to whatever value we give it. JavaScript will say: "OK, this time through, `xxx` equals that thing you passed in. Now I'll run the rest of the code between the curly braces."

We can also use multiple parameters separated by commas. JS will hand out the names in order:

```javascript
function megaparams(a,b,c) {
    // some code!
}

megaparams(333,'hi',null)
// a = 333, b = 'hi', and c = null

megaparams('XXXX',77,0)
// a = 'XXXX', b = 77, and c = 0
```

## Returning values

JavaScript will totally do whatever you tell it to do. If you write it between the curly braces, JS will try to do it when you invoke the function.

One awesome thing we can tell a function to do is *return* a value. After it has done all the stuff we told it to do, the function can send a value back out into the wider JS world.

```javascript
function returner(name){
    console.log('Name provided: ',name)
    console.log('Thank you for providing your name.')
    console.log('Regardless of your input, we'll be sending out the number 999.')
    console.log('Just because!')
    return 999
}

const checkIt = returner('Jeremy')
```

When we invoke `returner`, it does everything we tell it to and then it *returns* the number 999 -- and we save that value as `checkIt`.

That means that `checkIt` is now equal to 999, because we told it to be equal to whatever was returned from `returner`.

Using parameters and `return`, you can ask JavaScript to do any processing you want. This function adds 9 to any number:

```javascript
function addNine(number) {
    return number + 9
}

const a = addNine(11)
// a = 20

const b = addNine(9)
// b = 18

const c = addNine(-12)
// c = -3
```

`addNine` does the same moves each time... but it gives a different result when we give it a different input.

One way to look at it is that when a function is invoked, three things happen:
1) The function takes note of what's in the parentheses, and assigns these values to their parameter names in order.
2) The code block -- everything between the parentheses -- runs! Anything can happen! Parameters are printed or manipulated! Hearts are broken! Worlds collide! Anything!
3) The function returns whatever we tell it to -- it can be any sort of crazy result from Step 2 that we want... we just have to say `return crazyResult` and it sends it out.

## Big ideas

* **A function is a name for a block of code** that's set up to execute when you want it to. Just call the name with `()`!
* **Functions can have parameters** -- these are the names that we attach to values that are passed into the function from outside. You can give them whatever name you want, and you can use them just like other variables!
* **Functions can *return* a value** of any datatype -- this is the information that the function sends *back* into the world once it's done.
