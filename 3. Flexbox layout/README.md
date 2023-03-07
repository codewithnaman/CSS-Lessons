# FlexBox

## Basic Concepts and Terminalogy
* Flexbox is all about the relationship between a parent cotainer and it's direct descendant child items.
* The parent container is known as flex container.
* The direct descendant of the container are referred to as the flex items.
* The Flex items flow along what is known as the main axis.
* Main start is found at the begining of the flex container, this is the point from where the flex items starts to flow.
* Flex items flow from main start to main end which is found at opposite site of flex container.
* The Flex container's cross axis runs perpendicular to main axis.

### Flex Container
* To establish a container as flex container we need to define display property as 'flex' or 'inline-flex'. 
* The container define with display property with value flex occupies the full width of screen; even if flex item content doesn't occupy whole space.
* The container define with display property with value 'inline-flex' occupies the only width in which it's flex items fit in.
* We can define how flex items will flow in flex container by using property 'flex-direction'.
* 'flex-direction' has valid values 'row','row-reverse','column' and 'column-reverse'.
* When there is not enough space to fit all content of flex items; then by default item will not be wrapped and extra content will be hidden.
* We can wrap the content of flex to next line if there is not enough space is avaiable by adding property 'flex-wrap'.
* 'flex-wrap' has valid values 'nowrap','wrap' and 'wrap-reverse';
* 'flex-flow' is shorthand for 'flex-direction' and 'flex-wrap'; it takes the flex-direction as first argument and flex-flow as second argument.


### Flex Item
* We can control the order of flex item using property 'order' in flex item css.
* By default all flex item have order property value set to 0.
* If we want to render an flex item towards main end then we will set order value to  1.
* The flex items are rendered in incremental manner of with respect to order value of flex items.
* If the flex items order values are equal then they are rendered as the element appear in HTML.
* 'order' value can be negative and valid.
* Don't use the property order when designing for accessiblity or keyboard navigation; as order only change the visual but not the structure.

#### Flexibility of Flex Items
* This is key feature of flexbox layout, which is ability to make flex items flex, to shrink and grow to fill available space within the flex container. 
* Flexibility is controlled on the individual flex items themselves.
* First we have the flex grow factor, which controls how much a given item in a row or column will stretch relative to the other items within that row or column in order to fill up the positive free space. 
* We can set the flex grow factor using the 'flex-grow' property.
* When we set the flex-grow factor on container level; then each element occupy the equal space in container to fill up the space.
* In case just say we want a particular item occupy more space then other items then we can set the flex-grow for that item level and can provide larger value given to container value.
* We have the flex shrink factor, which uses the flex‑shrink property. This property is the opposite of the flex‑grow property. It controls how the space is distributed when there's not enough space for the items to fit. 
* If we set flex‑shrink  to 0, we'll see that it maintains its original size, the width that we set, while the others shrink. 
* We have the flex‑basis property. Flex‑basis sets the initial size of the items before the extra space is distributed. 
* flex‑basis shares many similarities with the width property, and in fact even uses the exact same length values, meaning pixels, points, ems, rems or percentages. 
* The shorthand property to define these 3 values is 'flex' property; which takes grow factor as first argument; shrink factor as second argument and flex-basis as third argument.

#### Flex Items alignment
* To vertically center an item within a given container, it required some very hacky CSS. Well, Flexbox leverages the CSS Box Alignment module, which allows us to use simple keywords to align items along the flex container's main and cross axis.
* Flexbox alignment can be handled in two different ways. It can be applied to all the flex items in a given container via the justify‑content, align‑items or align‑content properties, or it can be applied to the individual flex items themselves via the align‑self property.
* The justify‑content property allows us to align the flex container's items along the main axis.
* The default value of flex‑start will place the items at the beginning of the main axis, known as the main start. 
* We can quickly reverse this by using a value of flex‑end instead. 
* We can easily center these items on it's main axis by applying a value of center to the justify‑content property.
* justify‑content also allows us to evenly distribute items by dividing up the extra space and adding it in between each of the items via the space‑between value. 
* Similarly, we can use the space‑around value to add space before the first and after the last item. The extra space is divided up and applied to both the left and right side of the flex items.
* align‑items property, which will align the flex items along the cross axis. If we set align‑items to a value of flex‑start, we can see that all the items are aligned to the top of the container. 
*  If we want to vertical align these items in the middle, well, we can do that too by adding a value of center. 
* If we need to align any individual item uniquely, we can do so on the individual item using the align‑self property.
* t's pretty nice and easy to align items when we have a single line of flex items, but what about when we have items that wrap onto multiple lines? Well, this is where the align‑content property comes in. It's used to align lines within a flex container along the cross axis when there's extra space available.
* Now, it's also important to note here that we have a method to easily add space between flex items. We can use the gap property. Gap is specifically tailored to add space between items, essentially gutters. So if we add flex: 1 to our items, they run into each other. To add some space between these items, we can add the gap property to the flex container. 

