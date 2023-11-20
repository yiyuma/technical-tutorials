## CSS (Cascading Style Sheets)
**CSS** specify how things should look in the website.<br>
Add CSS
- Inline: use it when you only want to target a single element.
  ```
  <tag style="css" />
  for example:
  <html style="background:blue"> //  background is a property. blue is the value.
  </html>
  ```
- Internal: can apply to anywhere in the HTML document. We can target or select as many elements as we want. It is useful when you only want to target a single web page.
  ```
  <style>css</style>
  for example:
  <html>
    <head>
      <style>
          html{background:blue;} // html is a selector
      </style>
    </head>
  </html>
  ```
- External: We can write a styles.css file external, and link it in the HTML document. Use it for multiple web pages.
  ```
  <link href="style.css"/>
  for exampl:
  index.html
  <html>
    <head>
      <link rel="stylesheet" href="./styles.css" />
      //rel is relationship, href is for the location.
    </head>
  </html>

  styles.css
  html{background:blue;}
  ```



**Web Hosting** is the process of making your websites available anywhere on the internet.
- Put our website and all of the files and folder (index.html. images, etc) onto a web server.
