# CSS Variable

# Achieve

Using **JavaScript** and **CSS** to drag the slider, adjust the `inner margin`, `blur` and `background color` of the picture in real time. At the same time, the `color of JS` in the title also changes with the background color of the picture.

View it online: [CSS Variable](https://kongpeter.github.io/JavaScript30/03%20-%20CSS%20Variables/)


# Characteristics Involved

* `:root`
* `var(--xxx)` CSS Variable
* `filter: blue()`
* Event: `change`, `mousemove`


# Programming

## CSS

* Declare the global CSS variable (`:root`) 
* Apply changed CSS value to the corresponding element `<image>` 
* Processing the value of title



## Update CSS by JS

* Get `input` element
* Add listening event to each `input` to trigger the update operation when the value changed
* Add event monitoring when mouse over
* Write methods to handle update operations
    * Get parameter value suffix
    * Get parameter name (blur, spacing, color)
    * Get parameter value
    * Assign value to CSS



# Basic knowledge

## NodeList & Array
You can open proto to view its methods, which including foreach(), item(), keys().etc. However, `Array`'s prototype contains only methods such as map(), pop(), etc.



## Custom data attribute in HTML5 `dataset`
In HTML5, you can add non-standard custom attributes for elements, just add the `data-` prefix. After adding, these values can be accessed through the element's `dataset` attribute, which is an instantiation object of domstringmap, which contains the "name-value" pair of the custom attribute set previously.


## CSS Variable
This is a new feature of **CSS3**, which is not supported by [IE or edge](https://caniuse.com/#feat=css-variables) at present. The naming method is `--variable name`. When referring to this variable, it is written as `var(--variable name)`. See the next code for specific examples.


## `:root` Pseudo-Class
 This pseudo element matches the root element of the document, which is the `<HTML>` tag.
 Therefore, it is commonly used to declare global CSS variables: 

```css
:root {
  --color: #fff;
}
```

When using it:

```css
img {
    background: var(--base);
}
```


## CSS Filter
CSS filters provide some graphics effects, such as Gaussian blur, sharpening, color changing, etc. It has some preset functions, which can be called with parameters. It is supported in [Chrome and Firefox](https://caniuse.com/#search=filter).



# Solving difficulties




