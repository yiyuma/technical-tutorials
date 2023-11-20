## HTML (HyperText Markup Language)
**HTML** defines the content and structure of the website.<br>
**HTML Tags**
- void element (self closing tag): It is element without content
  ```
  - <hr /> or <hr>: horizontal line element
  - <br /> or <br>: break element
  - <img />: element for image.
    attribute:
    scr: source. <img src="location of image" />
    alt: alternative text description. <img src="URL" alt="description of the image" />
  - <meta>:
    attribute:
    charset:
  ```
- no void element: it has content between opening tag and closing tag.
  ```
  - <h1></h1> to <h6></h6>: HTML section heading elements. They represent six levels of the sectin heading. h1 ist the highest section level and h6 is the lowest.
  - <p></p>: paragraph.
  - <ul></ul>: unorder list. The list items in the unorder list will be listed with bullet points.
  - <ol></ol>: order list. The list items in the order list will be listed with numbers.
    -<ol start=5></ol>: the order list will be started with number 5. 
  - <li></li>: list item.
  - <a></a>: anchor tag will give us a link to a web page or something on the internet. The additional attribute will be added in the opening tag. 
    - form: <tag attribute=value anotherattribute=value>Content</tag>
    - attribute:
      href: the URL that the hyperlink points to. <a href="www.google.com">google</a>
      draggable: to drag the element. <a draggable=true></a>
  - <html></html>: html tag, It is the root of the document.
    - attribute:
      lang: language of the text conten in the element.
  - <head></head>: important information about the website. not display for the user.
  - <title>title in the </title>
  - <body></body>: content of the website.
  ```


- button
- canvas
- div
- em
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
- strong
- style
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
