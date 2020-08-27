# 02 JavaScript CSS Clock

## Achieve results

The HTML structure has been given in the document. There are three ``div``, `hour-hand`, `min-hand` and `second-hand`. Just add some CSS to change the style of the clock, use JavaScript to update the state of the pointer.

View it online: [JS-Clock](https://kongpeter.github.io/JavaScript30/02-Clock)




## Key Points

1. The style of the pointer on the clock face. 
2. The effect of rotation gets the real-time time.
3. The state of the pointer is updated every second.


### Corresponding Characteristics

- `transform-origin`
- `transform: rotate()`
- `transition`
- `transition-timing-function: cubic-bezier(x, x, x, x)`
- `setInterval(callback, time)`
- `new Date()`


## Programming

### CSS

1. Adjust the initial position of the pointer and the pivot point of rotation [transform-origin](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-origin)

```css
transform-origin: 100%;
```

2. Adjust the transition reaction when the clock pointer is running. 

```css
transition: all .5s;
```

3. Add a center point to the dial with a pseudo element.

```css
.clock-face:after {
width: .8em;
height: .8em;
left: 50%;
top: 50%;
position: absolute;
display: block;
transform: translate(-50%, -50%);
content: '';
background-color: #a8c5d1;
border-radius: 50%;
box-shadow:
0 0 0 2px rgba(0,0,0,0.1),
0 0 10px rgba(0,0,0,0.2);
}
```


### JavaScript

1. Using the timer to automatically update the time, the timer `setinterval` can put the operation into the execution queue at a fixed time. With this feature, the time would be updated per second.

```css
 setInterval(setDate, 1000);
 // setDate execute the function after every 1000ms
 ```

2. Get the HTML elements corresponding to the three pointers for subsequent operations.


3. Program function `setDate`\
    * Create object `Date`
    * Obtain hour, minute and second.
    * Use the current time info to calculate the angles of three hands.
        ```css
        const secondDeg = 90 + (second / 60) * 360;
    Take the second hand as an example. Since the second hand is horizontal in the initial state of this page, the rotation angle applied to the element at zero (time start position) should be 90 degrees. It takes 60s for the second hand to turn once, so the angle value on the dial corresponding to each second is $(... S / 60s) * 360 °$.

    However, in the solution given by Wes BOS, the hour hand jumps every hour like the second hand. To simulate a more real clock, this clock should move slowly to the next time point in an hour. So we can use the last minute to calculate the effect of each minute on the angle of the hour hand, which will be added to the angle of the hour hand.

    ```css
    const hourDeg = (90 + (hour / 12) * 360 + (min / 12 / 60) * 360);
    ```
    * Assign the angle value to the `transform` of `style` in HTML.
