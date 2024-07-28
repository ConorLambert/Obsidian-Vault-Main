
# CSS Fundamentals

#### Collapsed Margins
- Please check this [[! Margin Notes]] for explanation on this.

#### Block Level Elements
- They have default width of 100%

#### Inline Elements
- You can only nest other inline elements inside an inline element.
- Only respects margin, padding and borders which are set on the right and left side on an element and not at the top or bottom.
	- Padding and borders on top and bottom do kind of work but with strange behaviour. It's like the other elements act as if the setting isn't there:
	 ![[Pasted image 20230830162859.png]]
- Width and height settings do not work.

#### Span Element
- Useful for decorating things and making them stand out. For example, accenting the color of some text within a paragraph.

#### Equivalent Specificity
- When two selectors are equivalent in specificity, the last one declared is chosen. 
- This is because the browser processes the CSS file from top to bottom.

#### Property Order:
- If the same property is set within the same selector block then the bottom most one is chosen.
- This allows for situations where we can set all margins to 0 and then below that in the same selector, set the **margin-bottom** to some other value.

#### Focus Pseudo Element (Links)
- Useful for tabbing through elements on screen.
- Very useful for Accessibility purposes.
- Focus and hover states tend to have the same styling

#### Active Pseudo Element (Links)
- Applies when clicking the link (the second the mouse is pressed down) and stays in this state until the user has clicked elsewhere on the same page.

#### Pseudo Selector Order (Links)
- The order of the pseudo selector declarations is important
- *An element can be in more then one state at the same time.*
- And when an element is in more then one state, the *Equivalent Specificity* rules apply.
- To make sure each state is styled properly then make sure they are declared in the following order:
	1. a
	2. a:link
	3. a:visited
	4. a:focus
	5. a:hover
	6. a:active
- For example, if `focus` is before `hover`, the `hover` style will never be applied. Likewise, if `a` was declared at the end than none of the other styles will apply as `a` overwrites all styling, including pseudo styles.

#### Inline-Block
- Same as an inline element but you can set the height, width, margins, padding and border on all sides.
- Useful for buttons
- The following two images show the effect of inline-block on two button elements that have padding properties set.
	- Top image has `inline` set. You can see the buttons are causing issues. The buttons are also bunched up against each other.
	- Bottom image is where `inline-block` is set. Noticed how much better they fit and how much better control we have.

![[Pasted image 20230831210824.png|300]]

![[Pasted image 20230831210402.png|300]]

#### Use `padding` for Buttons dimensions
- Always use `padding` to create the "size" of a button and not `width` and `height`.
	- Problem with using a set width for example is some buttons can have longer text. You could end up with the following effect:
	![[Pasted image 20230831212153.png|300]]
	- Notice the text of the right side button is squished.
- The padding on the left and right need to be a bigger number then the top and bottom
	- *A general (but not strict) rule is to use a **1:2** or **1:2.5** ratio*. But adjust until it looks right.

#### Selector Specificity
- Selectors from lowest to highest:
	- Element
	- Class
	- ID

#### Selector Advise: Go with classes
- Many company naming conventions only use classes. Otherwise it can complicate things in the long run when trying to find out what selector is being used.

#### Headers Best Practices
- Have one `h1` element per page on a site
	- Place this inside a `header` element

#### Compound Selectors
- Using two or more selectors together to style an element
- Very good for situations like the bottom two sections of the below image.
- They both have the same structures but the colours and styling change a little bit:

![[Pasted image 20230904204954.png|300]]

#### Compound Selectors and Specificity
- CSS specificity is implemented based on a point system:
	- Element = 1
	- Class = 10
	- ID = 100
- When we combine these together using Compound Selectors, the total sum is used to decide its specificity. 

#### Compound Selectors Performance
- Can cause performance issues due to how the browser handles compound selectors
- Read from right to left.

#### Strive for using Single Classes
- Generally, we want to avoid compound selectors because they can become complicated to read later on
- *Give everything a single class*
- Note that this rule is not saying that an element should only have one class.

#### Generic Class and Modifier Class
- If two elements share similar stylings then create a generic class that can be used by both elements.
- The unique styling of each element can be declared under their own modifier class.
- For example, a `.container-nav` could be a modifier class to a `.container` class that applies changes to some property of the general `.container` class to suit that specific element. 
- A modifier class is also good for things that may change. Maybe you want to try a certain navigation out. Rather then putting it into the general class, put it into a modifier that can easily be deleted later if it's no longer viable

#### Font Stacks
- Problem with setting a font family is that the font will only work if the visitor has that font installed on their computer
- Font stacks solve this issue by allowing the developer to declare backup fonts that will be used in the event that the visitor does not have a higher listed font installed.

#### Google Fonts
- Hosted on google so users machine will automatically download the font if not installed.
- Developer links to the hosted site via the `link` element inside the `head` element.
- We also need to tell Google Fonts what weights and styles we will be using.
	- Forgetting this will result in your bold and italic styles no longer working
- *Fonts are one of the heaviest thing to download and if you have selected multiple types of weights, etc then this can cause the download size to increase dramatically*
	- This also results in a shift on initial page load where the default font is shown and then it shifts to the correct font after it has downloaded.
- Google Fonts are cached though so if a user has visited your site before or visited another site with the same font then it doesn't need to be downloaded again.

#### Inheritance
- Most properties are inherited from their parent elements.
- Set font-family on the body element and it will flow through the entire document.

#### Inheritance and Links
- Links do not inherit the `color` and `text-decoration` properties from their parent element because link elements have default values set for these properties.

#### Inheritance and Headings
- Headings (h1,h2, etc) do not inherit the `font-weight` from their parent because they have a default value of `bold` set.

#### `inherit` Property Value
- We can force an element to inherit the property of its parent element by declaring the value `inherit` for whatever property we are targeting:
	![[Pasted image 20230905211700.png|150]]
- All properties have an `inherit` option.

#### Container Wrapper
- The author prefers to wrap the site content in a `div` element that sits directly underneath the body.
- Uses this container to control width of the content.
- Prefers this approach then setting with this on the `body` element because at a later stage, an element may be added that is required to take up the whole width of the page.

#### Putting it all together exercise
- A good approach to CSS is to code it all out first even though it is duplicated. Then remove the duplication.
- Use a `.container` div that wraps content for the purpose of centering the content as was shown in the exercise
- Set the default font properties in the body selector so that each other element inherits these values
	- Font family, 
	- Font-size
		- The size will not be inherited by h1, h2, etc
		- Set it to the normal text size i.e. paragraphs, etc
- Put main text color in the `body` selector.
- The heading elements i.e. h1, h2, etc have a default margin value greater then 0 which can interfere with your layout (particularly in cases where you use padding to provide spacing).
- White border appears around the body element which is problematic
	- Solution is to set `margin: 0` on the `body` selector.
- Section your CSS with the use of comments. For example, place a comment called `Typography` above the group of selectors related to typography. Place a comment called `Layout` above the group of selectors related to layout.
- Use `<header>` element for main title of a page.
- Don't forget to set the `alt` attribute on images.



# Starting to think responsively

## Units
#### Percentages
- Mainly used for widths
- Relative to their parent
- The behaviour is strange on heights.

#### Relative Units
- Relative to something else:
	- Font-size
		- `em` and `rem`
		- Font-size is inherited from the parent (all the way back to the body element if no font-size is defined).
	- Viewport
		- `vw,` `vh`, `vmin`, `vmax`

#### Don't use `em` for font-sizes
- The cascading effect can make your CSS complex to deal with.

#### Use `rem` for font-sizes
- `rem` stands for **Root** `em`
- It's relative to the *root* of the document i.e. the `html` tag
- This means we can set a font-size on the `html` element and then any piece of text can scale up or down against that value using the `rem` unit.
- This is much easier then `em` because we only scale against one value which avoids the cascading effect

#### Pixels are a fixed unit, not a dot on the screen
- Like an inch or centimetre. 
- Wasn't always the case though, which is why `em` and `rem` came about.

#### Pixels have improved
- People use to avoid using pixels but its new design makes pixels easier and more responsive to use. 
- Setting a value of say 16px should make it look relatively the same on different screen resolutions.

#### `em` on non font-size elements
- If `em` is used on a non font-size element such as `padding`, then it's size is relative to the font-size of the same element and not the parent.
- It could be mistaken as being taken from the parents font-size but because of inheritance, the current element will take it's font-size from the parent unless the current element has overwritten it.

#### Units General Rule of Thumb
- Not hard and fast rules
- rem
	- font-size
- em
	- padding
	- margin
- widths
	- px
	- em
	- percentage

#### em for padding and margin
- Allows buttons to scale up based on the `font-size` of the current element.
- Don't have to keep changing the padding/margin pixels for different screen sizes 
- Different screen sizes will absolutely require different font-sizes. It's the main thing that changes.

#### Default Font-Size
- 16px
- Set on the `html` element

#### Warning
- When using `em`, always be sure of what class defines the font-sizes that are used as the base. They could be defined in a different class like below

	![[Pasted image 20240626143210.png|150]]

- The padding of the `.button` class uses `em` but the font-sizes which forms the base value are declared in different classes i.e. the `.btn-small` and `.btn-big` classes.
- In the HTML, the `.button` class is applied to the same elements that `btn-small` and `btn-big` are applied to.
- Can be difficult to debug.

#### Widths of Images
- Images are an inline element
- This means they are not defaulting to 100% width.
- Images default to the size of themselves i.e. the size of the original image.
- You can end up with the following issue:
	![[Pasted image 20230911195554.png|300]]
- To solve this issue, we set **width: 100%** on the img.

#### Width and Height of Images
- Don't set the width and height properties of an image at the same time
	- Only set one of them
- Setting both can distort the image
- If we set one of either then CSS will deal with the other property to maintain its ratio.


## Flexbox

#### Example/Exercise: "Basic styles and setting up columns"
- Mistakes Made:
	- Forgot to set `margin: 0` on `body` element
	- I incorrectly used the `width` property for the container. 
		- Should have used the `max-width` property instead.
		- Check [[width vs max-width]] for more info
	- I set body font-size (1.125) on the `p` element but I should set this on the `body` element
		- Remember, the default font-size is defined on the root `html` element.

#### Flexbox Gaps Examples 

###### Center Based
![[Pasted image 20230915172124.png]]
- `justify-content: space-between`
- Use `em` on the `margin-right` property
	- Something like  `margin-right: 1em`  will suffice.
- This approach works because the last element has nothing to its right.

###### Navigation
- Same as **Center Based** but use `margin-left`
![[Pasted image 20230915172048.png]]
	
###### Paragraph Columns
- `justify-content: space-between`
- Create a class for each column width needed using percentages
	- .col-1 { width 25% }
	- .col-2 { width 50% }
	- .col-3 { width 75% }
- Apply these classes to their corresponding columns
	- Column "Dolor sit" and the last column would get `.col-1`
- Do the following to create the gaps between each column: 
	- Take 5% of the width of each column class. 
	- For example, change width of `.col-1` to 20%.
![[Pasted image 20230915130428.png|400]]

#### Flex: baseline
- Aligns the top level element of each box with the tallest of those elements.

#### Orientation: Landscape vs Portrait
- Landscape: Something is wider then it is tall.
- Portrait: Something is taller then it is wide.

## Media Queries

#### Media Queries Selector Order
- The order you place your media queries is important
- One or more media selectors can be in the same state at the same time
	- Think of a media selector with `min-width` set

#### Media Queries Placement Options
1. Bottom of the CSS sheet.
2. Under the selectors its related to.
	- Preferred approach according to author

## Other Stuff
#### Don't use h2 for a sub-title
- H2, H3, etc are for headings in different areas of the site.

#### `ul` has default padding
- `ul` elements have a default padding to make space for the list items

#### `text-align: center` important
- This centres the text within that texts parent element.
```html
<div> <!-- This is the parent element -->
	Some text 
</div>
```

#### `:hover` and `:focus`
- Whenever you style `:hover`, make sure you style `:focus`

#### Don't be afraid to use magic numbers for widths and spacing
- Most of the time its needed

#### Mobile First Design More Common
- Mobile first design is a more common approach to building UIs
- When we say Mobile First, *we are talking about the CSS*
	- This includes media queries
		- Go for `min-width` media queries instead of `max-width`.
- When it comes to the HTML content, we go by desktop design first.

#### Why Mobile First
- Mobile screens tend to be easier to style
- Generally, if we start with mobile first when styling then overwriting (using media queries) will result in less CSS code.
- This [video](https://v1.scrimba.com/learn/responsive/starting-to-think-mobile-first-cvzLepT8) on Scrimba explains it well

#### Every website should have a `main` element
- Very useful for accessibility purposes
	- Some assisted technologies even start reading from the `main` element
- There should only be one `main` element

#### Class naming convention
- Prefix of the class name should be based on the element
	- `btn` for a `button` element
	- `article` for `article`
- The suffix should based on the purpose of that element or elements
	- `btn-general` for a general class
	- `btn-smaller` for a modifier class

#### Element Order and Accessibility
- Its common for developers to lay out the HTML elements in the order they appear on screen but we don't have to do it this way.
	- If we have less useful information above more important information in the design (even though its smaller in size) this could effect things like assistive technology and badly loaded pages.
	- For example, an image could be before the h1 element in the design but we can layout the HTML so the h1 is before the image. Putting the h1 element first is better for badly loaded pages and assistive tech.
- We can use the flexbox `order` property (on the element, not the parent). 
	- The lower the number, the earlier it will appear:
```css
.article-recent-main {
    order: 1;
}

.article-recent-secondary {
    order: 1;
}
```

#### Start with Typography
- When styling with CSS, start with your typography first i.e. font-sizes etc
- If you start your typography later on in the process, you may run the risk of having to keep changing the layout as you begin changing other things like spacing, layout, etc.

#### After Typography, Do Big Layout
- First step when styling is to do Typography
- After that, do Big Layout
- Then lastly, work on gradually smaller aspects.

#### Default Font Size
- The default text size in browsers is **16px**. So, the default size of 1em is 16px.

#### Common `img` Style
- It's always good to set this styling on your image by default in your css file:
		![[Pasted image 20230925171931.png]]
- Common to see this in most CSS projects
- Put this under body selector in CSS
	- It's a more general setting

#### Use of Border Property
- The following image shows an **About Me** and **Recent Posts** section on the right side:
![[Pasted image 20240709160108.png|500]]
- To achieve the grey surrounding area, use the `border` property like so: 
```CSS
.sidebar-widget {
	border: 20px solid #efefef;
	margin-bottom: 2em;
	padding: 1em;
}
```


#### Use of `meta viewport` element
- Without the following line in our html file, responsive design and media queries will not be applied:
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
- Explained better in Scrimba [video](https://v1.scrimba.com/learn/responsive/important-note-the-viewport-meta-tag-cN3pGPSN)


## Project Attempt
#### `<ul>` defaults
- `padding-left` = 40px;
	- [Source](https://stackoverflow.com/questions/30424248/does-ul-have-default-margin-or-padding)
- The `<ul>` and `<ol>` elements have a top and bottom margin of 1em.
- For example, if `font-size` of text in `<li>` is 18px, then `margin-top` and `margin-bottom` are 18px also. 
- Note the above may differ in other browsers

#### Add padding to `<a>` element
![[Pasted image 20240724195024.png]]
- Adding the padding to the `<a>` element so that the underline applied to the selected page is moved away from the text.
- Adding the padding to the `<li>` element would not result in this effect.

#### Certain letters can give a natural margin
![[Pasted image 20240724194753.png]]
- There is no margin or padding applied to either of the above pieces of text
- It' the letter `g` in the top line that is pushing the below line away and providing a nice space naturally.

#### `.container` element width explained
```css
width: 90%;
max-width: 900px;
margin: 0 auto;
```

**width: 90%**
- Is used only for smaller screens. 
- It provides space between the left/right parts and the edges of the screen.

**max-width: 900px** 
- Maintains that desktop look where the content sits in the centre and there are two big massive gaps on the left and right of the screen.

#### .container-flex multi-purpose
- The `.container-flex` class is managing the `flex-direction` of both `header` and `main` so that on smaller screens, they both collapse their content into a `column` but on larger screens they are `row` based.
