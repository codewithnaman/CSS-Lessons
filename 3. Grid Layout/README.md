# Grid Layout

## Basic Concepts and Terminalogy
* Flexbox and CSS Grid share some similarities, but the main difference is that Flexbox controls how items flow in one dimension, whereas Grid controls how items flow in two dimensions. 
*  Flexbox items flow in a similar fashion to the way that text content flows on the web, meaning that items flow in a straight line in one dimension or in a broken line if there's not enough room and they're allowed to wrap. Flexbox is great at handling alignment, distribution, and order of content and space. CSS Grid, on the other hand, is suited to lay items out in both dimensions.
* The core difference between Flexbox and Grid is that Flexbox lets content size itself based on the space available or the dimensions of the content itself, and Grid specifies nothing about how the individual items themselves should be sized and instead relies on various grid lines being defined on the grid container for its sizing info. 
* CSS Grid, like Flexbox, is all about the relationship between a parent container and its child items.
* This parent container is known as the grid container, which contains what are known as grid items. This parent container is known as the grid container, which contains what are known as grid items.
* A grid is made up of two sets of lines, known as grid lines. One set of lines defines the columns for the grid. These lines run along what is known as the column axis. Then, there's another set of lines that defines the rows for the grid, and these lines run perpendicular to the column axis along what is known as the row axis. These grid lines together make up what are known as grid tracks.
* They are created by the space between two consecutive row or column lines and are given a size, which controls how tall a row can be or how wide a column can be. Where grid rows and grid columns intersect is where we find what are known as grid cells, and these are similar to table cells and are the smallest units of the grid that we can place items into. 
* We have what are known as grid areas, which are essentially any portion of the grid that is contained by four grid lines.

### Grid Container & Grid Items
* To establish a container as grid container we need to define display property as 'grid' or 'inline-grid'.
* To define our grid columns, we will use the grid‑template‑columns property. This will take the width of column in px, percentage and fr(new unit introduced) for each column.
* To define our grid rows, we will use the grid‑template‑rows property. his will take the height of column in px, percentage and fr(new unit introduced) for each row.
* The next step is to place our items into these areas that we've defined. This is done by specifying at which grid lines they should begin and end. We do this by calling each item individually, giving them grid‑column‑start, grid‑column‑end, grid‑row‑start, and grid‑row‑end values.
* If we want some space between the cells, then we can use the gap property like we did with Flexbox. To give different gap for rows and column we can use property column‑gap and row‑gap properties.
* We defined a grid by explicitly defining rows, columns, and their heights and widths, and then manually placing these items into these rows and columns. Sometimes, We may just want to have grid items that are automatically placed into cells on our grid. If we do not declare item position on the grid, then it will use what is known as the grid auto placement algorithm and automatically size and place items. 
* This auto placement is that items flow horizontally from left to right along the row axis, and then top to bottom. This is because there is a grid‑auto‑flow property, which defaults to a value of row. If we needed to switch this, we could do so by switching this grid‑auto‑flow property to a value of column. 
* If we want to move to the location grid item in auto placement grid then we need to change the order of them, we can do so using the order property that we saw and used with Flexbox in the previous module. If we recall, all items have a default order of 0, so if we want to rearrange them, we will need to give them either a positive or negative value other than 0, and then these items will be moved either before or after all other nonplaced items. 
* With the auto grid features, we also have a notion of implicit grid lines. These are grid lines that we have not explicitly defined ourselves using grid‑template‑rows and grid‑template‑columns. 
* Implicit grid lines are created when we place an item inside a grid track outside of these explicitly defined grid lines.

* Shorthand for all above properties:
    * We can avoid defining grid‑template‑columns and grid‑template‑rows individually. We can actually define them both in one line using the grid property on the grid container. In order to do this, we need to first add our row values, followed by a slash, and then our column values.
    ```text
        grid: column column/row row;
    ```
    * There's really no reason to define a grid‑row‑start or end or grid‑column‑start or end because we have the grid‑row and grid‑column properties. These properties work by accepting both the start and end values for the item divided by a slash.
    ```text
        grid-column: start/end;
        grid-row: start/end;
    ```
    We may not even need the two different column and row properties because we also have a grid‑area property that will accept all four values. The order of these values is row‑start / column‑start / row‑end / column‑end. 
    ```text
        grid‑area: row‑start / column‑start / row‑end / column‑end
    ```
    
    * We can also take advantage of the span keyword to control how our grid items span across grid lines. With span, we still need to tell the item what grid line we want it to start on. But then we can use the span keyword with a value that will let the browser know that we want this item to span this many grid tracks, and it can be used either in the column or row direction.
    ```text
        grid-column: start / span number-of-columns;
    ```
    * We have repeated patterns, we can use the repeat keyword to repeat grid tracks without defining each grid line individually. Repeat works by setting the number of times that we want a pattern to repeat, followed by the actual pattern to repeat.
    ```text
     grid: repeat(3,100px) / repeat(3,500px);
    ```

### Custom named grid line and grid area
* Using the grid shorthand properties and keywords is a great help. It makes code much more simple, clean, and easier to read. But we may find that when we need to target specific grid lines for grid item placement, referring to these lines by number makes it more difficult to use because we always have to count the lines to know which ones we need. 
* CSS Grid allows us to name our grid lines whatever we want instead. We do this by adding our grid line names inside of square brackets in the grid containers grid‑template‑columns and grid‑template‑row properties.
```text
grid‑template‑columns: [main-content-start] 25px [main-content-end] 750px [sidebar-start] 775px [sidebar-end];
```
* Then, when we want to place our individual grid items on these lines, it makes it easier for us to find what we're looking for. 
```text
grid-columns: main-content-start/ main-content-end;
```

* Creating custom names for our grid lines can certainly make our code easier to work with in many cases, but we can expand on this and create custom named grid areas to place our items into as well. 
* In order to create a named grid area, we have to define the name grid area on our elements within the grid‑area property before we define our grid.

Example:
![Grid Area](images/Grid%20Area.jpeg)
```text
 Let's apply this to a media object example. Let's say that our media object has a title, so we create a grid area named title on the title selector. Then, we have a thumbnail, so we create a grid area named thumbnail on the thumbnail selector. And then we have a content section, so we create a grid area named content on the content selector. Next, we set up our grid. After this, we use our custom named grid areas with a new property, grid‑template‑areas. Here, we want our title section to be on its own row stretching the width of the grid. In order to do this, we repeat its name once for each column inside quotes. By repeating its name for each column, we are telling the browser that we want the item to span these grid tracks. We want a gap between the columns and rows, so let's add it using gap. Now, we want to add our thumbnail in the next row, followed by our content. We create this new row with a new set of quotes, then we add our thumbnail area, which will be placed in the first column, and our content area in the next column. There, everything is placed as needed. However, if we had the need for more complex grid spacing, we can achieve this by creating empty rows and empty columns. First, we can remove our gap style. Next, we need to add the empty row for our horizontal spacing. Let's make that 1em. Then we need to add the empty column to our grid. Let's make it 1.5em. Then we will want to add a row for horizontal spacing between the title and content in our grid template areas. This is done by adding a new set of quotes, and inside of these quotes we need to let the browser know that all of these grid cells should be empty, and that's done by adding a period. We need to be sure to add a space in between these periods because that's how the browser knows that the grid track begins and ends. If we run them all together, their grid will just associate them as a one‑column designation, which is not what we want. We then add a period for our gutter since we want some space between the thumbnail and the content. There, now we have a method to provide spacing in more complicated scenarios. So naming our grid lines and grid areas can provide clarity and intent that will make it easier to come back to this code later on and quickly get up to speed with what's going on. So now that we've got a grasp on naming our grid lines and grid areas, let's take a look at a few more items unique to CSS Grid Layout, auto keyword, the fractional sizing unit, and overlapping and layering items.
 ```

###  Auto, fr, & Overlapping/Layering Items
* Let's see how grid tracks work with the auto keyword. Till now we have explicitly defined the width of our grid columns and the height of our grid rows. This can make things fairly rigid, which may be okay, but sometimes we will not want this. 
* Sometimes we will want rows and columns to be auto sized based on the height or width of their content. This is where we can use the auto keyword.
* For example in a grid, we have a row that's going to have some dynamic content, so we set it to auto. Then, the row will size itself based on that content. If the content becomes longer, the row will grow in height. This also really lends itself to responsive design because when the viewport shrinks, the content wraps and becomes taller. If it was a fixed height, it would likely break at some point.
* We also have the fractional sizing unit, fr. The fr unit, like auto, can be used to size grid rows and grid columns. It's used to size a grid track based as a fraction of available space. 
* what if we need elements nested within another container to be part of the grid? Well, we can do this with display contents. Adding display contents to our nested element container will make it appear as if it is completely invisible from the layout engine in our browser. This allows the children within this container to be placed on the grid now.


### Grid Layout & Box Alignment
* Box alignment is a specifications independent of Flexbox and Grid and is intended to generalize the alignment of items within their containers. Since we've already seen how it works with Flexbox, we'll now take a look at how it works with Grid.
* The properties that can be applied to the grid container are justify‑content, justify‑items, align‑content, and align‑items. 
* If we apply the align‑content property with a value of center, we can see that this has changed the way that our grid looks. It actually took all of the items and vertically aligned them in the middle of the grid container. 
* If we were to change it to justify‑items,that will horizontally align the items based on the column that they're in.
* We can also apply box alignment to the individual grid items themselves if we need to control them individually. The properties that are applied to the grid items are justify‑self and align‑self.

