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

Using the timer to automatically update the time, the timer `setinterval` can put the operation into the execution queue at a fixed time. With this feature, the time would be updated once per second after adding the page to realize the effect of second hand rotation.


