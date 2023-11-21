## HTML (HyperText Markup Language)
**HTML** defines the content and structure of the website.<br>
**HTML Tags**
- void element (self closing tag): It is element without content
  ```
  - <hr /> or <hr>: horizontal rules, it defines a thematic break.
  - <br /> or <br>: break element
  - <img />: element for image.
    attribute:
    - scr: source path. <img src="location of image" />. You can use absolute path or relatives path as the value for the src.
    - alt: alternative text description. <img src="URL" alt="description of the image" />
    - width: width of the image in pixels
    - height: height of the image in pixels
  - <meta>: meta information
    attribute:
    - charset: charset="utf-8"
  ```
- no void element: it has content between opening tag and closing tag.
  form: <tag attribute=value anotherattribute=value>Content</tag>
  ```
  - <h1></h1> to <h6></h6>: HTML section heading elements. They represent six levels of the sectin heading. h1 ist the highest section level and h6 is the lowest.
    attribute:
    - style: style="font-size:60px;"
  - <p></p>: paragraph. A paragraph starts always on a new line.
    attribute:
    - style: styles to the element. color:red, font, size, etc
    - title: defines extra information about the element. It will be displayed as a tooltip.
  - <ul></ul>: unorder list. The list items in the unorder list will be listed with bullet points.
  - <ol></ol>: order list. The list items in the order list will be listed with numbers.
    -<ol start=5></ol>: the order list will be started with number 5. 
  - <li></li>: list item.
  - <a></a>: anchor tag will give us a link to a web page or something on the internet. The additional attribute will be added in the opening tag. 
    attribute:
    - href: the URL that the hyperlink points to. <a href="www.google.com">google</a>
      draggable: to drag the element. <a draggable=true></a>
  - <html></html>: html tag, It is root element.
    attribute:
    - lang: language of the text conten in the element. lang=en, or lang=en-US(Country code)
  - <head></head>: It contains meta information about the website and will not display for the user.
  - <title>title for the html page</title>: It will be displayed in the browser's title bar or in the page's tab.
  - <body></body>: defines the contents of the website.
  - <pre></pre>: defines preformatted text. It is displayed in a fixed-width font, and it preservess both spaces and line breaks.
  ```

HTML attribute
```
- style
  <tagname style="property:value;"> // property is a CSS property (background-color, color(text color), font-family, font-size, text-align), value is a CSS value.
  
```
HTML Text Formatting
```
- <b></b>: defines bold text
- <strong></strong>: defines important text
- <i></i>: defines a part of text in an alternate voice or mood
- <em></em>:
- <small></small>:
- <mark></mark>
- <del></del>
- <ins></ins>
- <sub></sub>
- <sup></sup>
```

- button
- canvas
- div

- embed
- footer
- form

- header


  
- iframe

- input
- label

- link

- nav

- option

- script
- section
- span

- textarea


**File Path**
- absolute file path
- relative file path: ../ means find file in the parent directory, ./ means find file in the current directory

**HTML Boilerplate**
```
<!DOCTYPE html> -- HTML Version 5
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Website</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```
