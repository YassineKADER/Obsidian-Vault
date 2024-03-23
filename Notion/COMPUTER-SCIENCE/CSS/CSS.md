# CSS Layout - float and clear:

---

The CSS `float` property specifies how an element should float.

The CSS `clear` property specifies what elements can float beside the cleared element and on which side.

## The float Property:

The `float` property is used for positioning and formatting content e.g. let an image float left to the text in a container.

The `float` property can have one of the following values:

- `left` - The element floats to the left of its container
- `right` - The element floats to the right of its container
- `none` - The element does not float (will be displayed just where it occurs in the text). This is default
- `inherit` - The element inherits the float value of its parent

In its simplest use, the `float` property can be used to wrap text around images.

**Example - float: right/left**

![[Untitled 27.png|Untitled 27.png]]

![[Untitled 1 8.png|Untitled 1 8.png]]

**Example - No float:**

In the following example the image will be displayed just where it occurs in the text (float: none;):

![[Untitled 2 6.png|Untitled 2 6.png]]

![[Untitled 3 6.png|Untitled 3 6.png]]

### The clear Property:

When we use the `float` property, and we want the next element below (not on right or left), we will have to use the `clear` property.

The `clear` property specifies what should happen with the element that is next to a floating element.

The `clear` property can have one of the following values:

- `none` - The element is not pushed below left or right floated elements. This is default.
- `left` - The element is pushed below left floated elements
- `right` - The element is pushed below right floated elements
- `both` - The element is pushed below both left and right floated elements
- `inherit` - The element inherits the clear value from its parent

![[Untitled 4 6.png|Untitled 4 6.png]]

---

# CSS Layout - The position Property:

The `position` property specifies the type of positioning method used for an element (static, relative, fixed,absolute or sticky).

## The position Property

The `position` property specifies the type of positioning method used for an element.

There are five different position values:

- `static`
- `relative`
- `fixed`
- `absolute`
- `sticky`

Elements are then positioned using the top, bottom, left, and right properties. However, these properties will not work unless the `position` property is set first. They also work differently depending on the position value.

### position: static;

HTML elements are positioned static by default.Static positioned elements are not affected by the top, bottom, left, and right properties.

An element with `position: static;`  
is not positioned in any special way; it is  
always positioned according to the normal flow of the page.  

### position: fixed;

An element with `position: fixed;` is positioned relative to the viewport, which means it always  
stays in the same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element.  

A fixed element does not leave a gap in the page where it would normally have been located.

Notice the fixed element in the lower-right corner of the page. Here is the CSS that is used:

![[Untitled 5 5.png|Untitled 5 5.png]]

### position: absolute;

An element with `position: absolute;` is positioned relative to the nearest positioned ancestor  
(instead of positioned relative to the viewport, like fixed).  

However; if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling.

**Note:** Absolute positioned elements are removed from the normal flow, and can overlap elements.

Here is a simple example:

![[Untitled 6 4.png|Untitled 6 4.png]]

```CSS
div.relative {
  position: relative;
  width: 400px;
  height: 200px;
  border: 3px solid \#73AD21;
}

div.absolute {
  position: absolute;
  top: 80px;
  right: 0;
  width: 200px;
  height: 100px;
  border: 3px solid \#73AD21;
}
```

### position: sticky;

An element with `position: sticky;` is positioned based on the user's scroll position.

A sticky element toggles between `relative` and `fixed`, depending on the scroll position. It is positioned relative until a  
given offset position is met in the viewport - then it "sticks" in place (like position:fixed).  

![[Screencast_from_10-16-2022_095152_PM.webm]]

![[Untitled 7 4.png|Untitled 7 4.png]]

# All CSS Positioning Properties:

![[Untitled 8 3.png|Untitled 8 3.png]]

[[CSS-GRID]]

[[CSS SELECTOR]]