# Basics

### Tip 1
Whenever is use the image optimise it double you want to show. Just say you want to show and image of 300px width; then try to use the 600 px width of better experience on web. The reason to use the double size image is to optimize image for the retina display which has 2 pixel for each pixel as compare to normal display.

## Selector
### Type Selector
Type selector are selector that directlly target the HTML elements like h1 type selector target all the h1 tag present in html.

### Universal Selector
Universal selector apply style to all elements present in HTML.
```css
* {
    border: 1px solid black;
}
```

### Class & ID Selector 
* class selector : class selector is the style you can use the class name to style element in the html. We can associate class with any html.
* id selector : id selector is similar to class selector. Just one limitation with the id is that id can apply to single element in a page while we can use class to multiple elements.

### Descendant Selector
Descendant selector is DOM render model. Which help to select the elements of html using tags in CSS. Let's first review below image and then will write some css to select the dom element and apply style to them.
![Descendant Selector](images/Descendant%20Selector.png)

here in diagram section is parent element and the h1,p,ul is descendant element of it. And h1,p,ul are the sibling element.

To Select a desendent we use the syntax below:
```css
section p {
    color: red;
}

section ul li {
    color: blue;
}
```
First code block change text color to red for the all paragraphs who is descendant of the section element. Second code block is descendant of descendant element section.

we can descendant different type of selector.

### Group selector
Group selector refers to apply style to multiple elements without writing the multiple code blocks; we can define that using comma separted selectors.
```css
h1, h3 {
    color: red;
}
```
above code change text color for the h1 and h3 to red.

### Combining selector
Combining selector is used when we want to style elements which pass all condition in combined way. For example if you want to apply style to a h1 element which has class alert only then we can use below block for such cases.
```css
h1.alert{
    color: red;
}
```

## Inheritance and Specificity
All CSS properties by default inherited to child elements from it's anestor elements. There are few exception in few properties which does not inheritated. Specifictiy define that if multiple styles are found for an element then in which order they are going to precedence. For this sceneario we use the below calculation.
1. Count the number of ID selectors
2. Count the number o class, attribute and psuedo-class selectors
3. Count the number of type and psuedo-element selectors

* The universal selector has a value of 0. 

Looking on above the most precedence given to css styles with ID selector then class selector then element selector and then universal selector.

* we use !important to push the css rule to apply; but if an element is marked two time !important then the later one will taken into account and then that styles will be applied.