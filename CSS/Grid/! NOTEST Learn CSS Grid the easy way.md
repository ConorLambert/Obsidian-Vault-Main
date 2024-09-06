[Source](https://www.youtube.com/watch?v=rg7Fvvl3taU)

### Don't need to define rows
- Recommends not to define the `grid-template-rows` property (apart from complex situations)
- Can just define the `grid-template-columns` property
- Avoids complexity and overhead.
- Grid will implicitly create more rows to contain the defined grid configuration.
- The row height in this case will be the height of the tallest element *on the same row* inside the grid.

### Spanning Columns
- Better to create a specific class for spanning columns e.g. a class that spans two columns:
```css
grid-col-span-2 {
	grid-column: span 2;
}
```
- Apply this class to the `div` contained within the grid

### Tooling
- Chrome can outline the grid including the line numbers.

### Start of easy, then get more complex
- Start as simple and generic as possible, then add the complexity as you need to, to be able to get the layout that you need.
- Example:
	1. Display grid
	2. Set the gap
	3. Set the columns (not rows)
	4. Then if you need to span individual cells across columns and rows, do that.

### nth-child property and cell order 
- The `nth-child` CSS selector targets the nth child in the order it's defined in the HTML not the order that the grid has possibly shifted it too.

### Line Numbers
- Don't let the line numbers trip you up
```css
grid-row-start: 1;
grid-row-end: 3;
```
- You may think the above setting will span two rows but it only spans one row
- You need to set the `grid-row-end` to `3` in this case.