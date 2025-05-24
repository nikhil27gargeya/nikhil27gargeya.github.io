# Frontend incl. React


CSS:  
Box model:
Margin (outermost), border (visible edge around the padding), padding (space between content and padding), content (innermost)

border-radius rounds the corner of this box
box-shadow adds a shadow to this box

Layout:
block: like layout sections
element will start on a new line and occupy full width available uneless changed
inline: like words in a paragraph 
element doesn't start on a new line, you cannot set width or height
inline-block: like buttons or images
formatted just like inline element but you can set weight and height values

Positioning:
static: default
absolute: positioned relative to neighbor
fixed: positioned relate to the viewport
relative: nudges element from normal positon

Flexbox (for arranging items in rows or columns, one dimensional):
align-content
align-items:
flex-direction:
justify-content: center (centers the grid items)

CSS Grid is two dimensional (rows and columns)

HTML:
```
<!DOCTYPE html>
<html>
<head><title>Title</title></head>
  <body>
  <h1>Heading 1</h1>
  <p>paragraphy</p>
  </body>
</html>
```

Javascript (adds interactivity to html)
Babel: javascript compiler
All React components require at least a render() function

class Header extends React.Component {
 render() {
 return (
   <div className="header">
     <div className="menuIcon">
     <div className="dashTop"></div>
     <div className="dashBottom"></div>
     <div className="circle"></div>
    </div>
   <span className="title">Timeline</span>
   <input type="text" className="searchInput" placeholder="Search
..." />
 <div className="fa fa-search searchIcon"></div>
 </div>
 );
 }
}

Singleton Pattern:
there is at most one instance of an object and the instance is ahred between all the processes that need it 


