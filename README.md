## Website Performance Optimization portfolio project

To run this file is double click on the index.html file
to open it up in a browser.

----------------------------

To optimize index.html, I put the images that were accessed through
several iterations of compression to shrink their sizes. I also inlined
minified versions of the css files and inlined the Google fonts link.

----------------------------

To optimize the the computation efficiency of resizing pizzas in pizza.html,
I reordered the actions performed in the pizzaElementGenerator function of main.js
so that all elements of the DOM are created, modified, and appended to the DOM first,
and then the style of their containers to optimize the Critical Rendering Path where
the CSS is changed at the end of the function since it calls Layout.

In the changePizzaSizes function, some of the computations were redundant and
could be shortened by simplifying the computation of the width, so I removed the
helper function that it used and simply did a batch change of style of the elements
being modified. I also switched some of the querySelector calls with getElementByClassName
or getElementById for simpler DOM traversal.

----------------------------

To optimize the frame rate for pizza.html, in the updatePositions function of main.js
I moved accessors to the DOM to the calling functions to reduce the number of times the
DOM is accessed. Then I computed the amount the page has been scrolled in one loop, followed
by a batch change to the style so that the style changes do not call Layout too early. Lastly,
I use the "translateX" function as opposed to accessing the "left" property of the style because
it does is easier to process.