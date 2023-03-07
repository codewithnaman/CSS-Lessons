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

### Pseudo-class selector
Pseudo class selector is used to change the styling dymanic like when user is interacting with the elements. For example hover, visited and active for links. The action are appended after the element or class seperated by : , then we can add property like normal classes.

## Inheritance and Specificity
All CSS properties by default inherited to child elements from it's anestor elements. There are few exception in few properties which does not inheritated. Specifictiy define that if multiple styles are found for an element then in which order they are going to precedence. For this sceneario we use the below calculation.
1. Count the number of ID selectors
2. Count the number o class, attribute and psuedo-class selectors
3. Count the number of type and psuedo-element selectors

* The universal selector has a value of 0. 

Looking on above the most precedence given to css styles with ID selector then class selector then element selector and then universal selector.

* we use !important to push the css rule to apply; but if an element is marked two time !important then the later one will taken into account and then that styles will be applied.

## The Box Model
For the browser every single element is displayed as rectangular box. This is known as CSS Box model. And it's a set of rules that define how elements are sized.

Before we go to the properties of box model. Let's understand how the elements occupy space. There are two types of HTML elements.

* Inline HTML elements: This takes up the same space as their content. Inline elements are displayed in a line from left to right. Inline elements will only wrap when items cannot fit.

* Block HTML elements: This takes the same height as content and same width as container. These always starts on a new line.

We can tweak behaviour using display property of html elements.

* **Inline display have no effect of change in height and width property.**
* **Inline-block will combine property of both block and inline element to show the element with inline space.**

Let's understand the Box model. Below are the properties which makes up the model.
* Content Box: The content box contains the actual content added between the HTML tags, such as text or an image.
* Padding Box: The padding area surrounds the content area, and this space is included inside of the element. 
* Border Box: The Border Box surrounds the padding area. 
* Margin Box: The margin surrounds the entire element. 

All four parts of these together determine the total area of each element. There are five CSS box properties. 
* Width is used to set the width of the content area. 
* Height sets the height of the content area. 
* Padding adds or removes the space within the element. 
* Margin adds or removes space around the element. 
* Border is added between padding and margin. 

* **Margin does not contribute to the total size of the element since it adds space around the element but it does effect the amount of space that the element takes up.**
* **Negative margin values are valud values while negative padding values are invalid.**
* **Use margin '0 auto' to center align element horizontally**

## Float and Position
Early websites are basically recreations of print designs. The float property allowed us to create magazine-style layouts with floated images and text flowing around those images. 

The majority of structural HTML elements used to create page layouts are block-level elements. So by default, they are displayed at full width and stacked on top of each other. The float property can be used to change the normal document flow by floating elements to the left or right side of its container.And when elements are floated, they are removed from the normal flow though they remain part of the flow, resulting in the change of the positioning of the surrounding elements. 

When we apply the float following elements will try to accompdate the space remaining from the float elements. Just say for an element we want to do left and another element to right. But post that any element we want to go back to it's normal flow. For that we need to applu 'clear: both' property.

The parent does not recognize the height of the floated element, and will only wrap around the elements that do not have a float applied to it. For example a div has 2 elements one is floated to left and second is floated to right. Then the height div will take 0 as it's not able to recognize the height of the floated elements. 
* If all the elements within the parent is floated, the height of the parent container will collapse to zero. As we see last example.

As long as there is space, the following containers, and all of its child elements, will try to stack underneath, as if the floated element wasn't even there. But the content will still flow around the floated element. In these scenarios, where there is no element to apply a clear to, we'll have to self-clear the float in the parent element instead. There are three options. 

* Use Overflow property to set how to show the content when it pass the defined value of parent container.
* css clearfix hack
 ```css
 .clearfix:after{
    content: "";
    display: table;
    clear: both;
 }
 ```
* Using the display property display:flow-root.

### Tip
* Using box-sizing: boder-box; we can make the box padding and dimension to include within the given width and height box size. This will fix the size with padding but not with margin as margin adds space around the element.

### Position
The position property can also be used to change the flow of the document. There are 5 different values. Each responsible for a different type of positioning. Static is the initial value, which means elements are not positioned. The 4 other values: relative, absolute, fixed, and sticky are positioned by arranging elements relative to its current position, its containing element, or the browser view port. For all of these values, except static, the top, right, bottom, or left properties must also be sued to specify the placement of the positioned elements. 

## Flexbox and Grid
Both Flexbox and Grid are new layout modules that can be used to create layouts that are more advanced than previous techniques. While they share some similar syntax and some of the same properties, they each have their own specialties. With Flexbox, items are aligned on a single axis. It is often described as being one-dimensional. While you can set the main axis to arrange items as rows or columns, Flexbox only deals with one dimension at at time. Grid layouts are thought of as two-dimensional, because it can arrange items into rows and columns at the same time. While both of these methods can be used for layouts, Flexbox is great for space distribution of items within the same axis. Grid is ideal for layouts that require more control with rows and columns. 
 
### Flexbox
#### Terminalogy
* Flex-Container: The flex-container refers to the parent element. 
* Flex-items: The flex items are the direct child elements within the flex-container.Flex items are laid out along the main axis. 
 
* The direction is horizontal by default, meaning flex items are arranged in rows.
* The cross axis will always run perpendicular to the direction of the flex items. Both axis also have start and end points. Main start and main end for the main axis and cross start and cross end for the cross axis.
* To use Flexbox, the flex-container must defined. For this we need to set display property to flex or inline-flex.
*  When display flex is added to the parent element, each child element is now a flex item. Flex items will automatically be displayed in a row and will be the same size as their content.  
* Also, with Flexbox the height of each flex item automatically adjusts to be the same height as the longest item without adding any additional CSS.

* The flex-direction property determines the direction of the main axis using one of four values, row, row-reverse, column, and column-reverse. Row is the default value. 
* By default, Flexbox only aligns the flex items on a single axis. If they're aren't enough flex items to fit within the whole container, there will be some space left. If the total width of the items are larger than the container, the items will automatically shrink to fit into one line. Nowrap is the default value meaning flex items will not wrap.
* Flex-wrap can also be set to a value of wrap. To layout the items over multiple rows, instead of shrinking to fit into one line, the items that do not fit will wrap to the next line.
* There are three properties used together to set the sizing of the flex-items. Flex-basis sets the initial size of the flex-items. Flex-grow determines how items will expand if there's extra space in the container. And flex-shrink determines how items will shrink if there isn't enough space in the container.
* The W3C recommends using the shorthand property, Flex, to avoid resetting any values that have not been specifically defined. To use the shorthand property, declare the grow value first, then the shrink value, ending with the basis value. The flex-grow and flex-shrink properties are defined with a unit-less numeric value.
* The flex-basis value may be used with link values, percentages, or key words
* Prior to Flexbox, there were options for center aligning elements horizontally, but getting elements to align vertically required a few hacks. With Flexbox, two properties were introduced to achieve this effect. Justify-content aligns items on the main axis while align-items is used for the flex items on the cross axis. To center align the item vertically and horizontally, set the values for both properties to center.


### CSS Grid
CSS Grid is a layout method that includes new CSS properties and rules that make it possible to create grid-based designs that previously required hacks and other workarounds.

* Grid Container: The grid container is the parent element. 
* Grid Items: The direct child elements are the grid items.

* Grid lines are the horizontal and vertical lines that divide the grid into columns and rows. Grid lines are also used to determine the position of the grid items and are referred to by a numerical index, or by custom name. 
* When using a numerical index, both the vertical and horizontal grid lines start at one. Grid lines can also be referred to by a negative numerical index which allows you to reference the opposite end of the grid.
* Grid lines are the horizontal and vertical lines that divide the grid into columns and rows. Grid lines are also used to determine the position of the grid items and are referred to by a numerical index, or by custom name. When using a numerical index, both the vertical and horizontal grid lines start at one. Grid lines can also be referred to by a negative numerical index which allows you to reference the opposite end of the grid.

* To define a specific number of grid lines and tracks, use grid-template-columns and grid-template-rows. This will create an explicit grid. These properties are declared in the grid container with the values expressed as a track list separated by a space to designate the number of tracks.
*  The grid layout introduced a new flexible length unit fr. This represents a fraction of the available space in the grid container. If the value of grid-template-columns is set to one fr three times that will split the grid into three equal columns, but if the value is set to 1 fr, 2 fr, and 1 fr, the grid items will still be arranged into three columns, but the second track will take up twice the amount of the first and third track. 
* We can also define multiple tracks using another value, the repeat function. Instead of writing 1 fr three times, include the number of tracks. repeat(3,1fr)
* Gutters can also be added between grid items using the gap property. One value adds the same amount of space between the rows and columns. Two values sets the gutter for the rows then the columns. Gap can be used with any length unit, the calc function, or a percentage but not the fr unit. The gutter space can also be declared independently using the longhand properties, row-gap and column-gap.
* When using a grid layout, grid template rows and grid template columns are used to define a fixed number of tracks to form an explicit grid. But sometimes you may have more grid items than the number of explicit tracks. For example, if you have dynamic content like a news feed, search results or a list of comments, you don't always know ahead of time how many items there are to display. Once an explicit grid is filled or if no explicit grid has been defined, the grid container will generate implicit grid tracks. 
*  If you don't know how many items your grid needs to display you can create the whole grid using only an implicit grid. And if you know the minimum amount of grid items you could use an explicit and implicit grid together. To define the size of the implicit grid tracks, use the grid-auto-rows and grid-auto-columns properties using the same values and syntax as grid template rows and grid template columns.
* So far, we've been looking at properties that are applied to the grid-container. These properties define the structure of the grid. Position-based properties must be applied to the grid items to determine their placement within the grid. The properties used for placing grid items are grid-column, which is shorthand for grid-column-start and grid-column-end, and grid-row, which is also shorthand for grid-row-start and grid-row-end. A number value is used to specify the the start and end of the grid-item's position based on the grid lines. When using the shorthand property, the value start and and end value must be separated with a forward slash. Let's take a closer look at grid-column first. Grid items, by default, start on line one and span the size of one grid cell. To change the start position, use grid-column-start, and to make the grid items span more than one column, use grid-column-end.