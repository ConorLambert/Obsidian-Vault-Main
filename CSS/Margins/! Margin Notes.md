#### Default Margin:
- The default margin of an element is the same as that elements current font-size.

#### Collapsing Margins (Siblings):
- Margin collapse occurs when *vertically* adjacent margins of block-level elements collide to share a general margin space. The size of this shared space is dictated by the larger number margin.
- Scrimba [explanation](https://scrimba.com/learn/responsive/margin-and-padding-collapsing-margins-c39EgLua).

#### Collapsing Margins (Parent-Child):
- Margins will collapse any time they touch each other. So, if the first child in an element has a margin-top, that can merge with the parents margin-top.
- This means if the parent element has margin-top: 0px and its immediate child element has margin-top:100px, then the 100px will be chosen because it is the larger number. 
- However, *this 100px will be assigned to the parent element and not the child.* This can cause unwanted behaviour if you don't fully understand this concept.

	**Padding to the Rescue**
	- If you want to avoid this behaviour then add some [[Padding/! Notes|padding]] to the parent element. This avoids the parent and child elements touching each other.
	- In this case, after the padding is applied then the child element will reclaim the margin of 100px.

#### Collapsing Margins with Flex-box and Grid:
- Margins no longer collapse when dealing with adjacent or parent/child elements where at least one of the elements has **display: flex** or **display: grid**.

#### Consistency:
- Consistency depending on Type
- Turn off the margin-top on typography elements e.g. headings, paragraphs, anything with text.
- That way we can use padding on the parent and keep spacing consistent on all sides.