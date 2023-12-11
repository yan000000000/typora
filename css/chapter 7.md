# lesson 7 styling link

---



### default for hyperlink

*   underlined
*   blue for unclicked, purple for clicked
*   cursor will turn into a pointer
*   when the cursor is hovering on the link, the link turn red









### basic

```css
a {
  text-decoration: none; delete the underline
  cursor: pointer;
  color: blue; change the color 
}


```

`cursor` it can change to many other



### pseudo class

```css
a:visited {
  color: purple;
}

a:hover {
  color: dodgerblue;
}

a:active {
  color: red;
}
```

`a:vistied` stands for pseudo class which its status can change, in this case, it set the visited website to purple

when you hover, it will turn blue;

>   the order is important, if you put hover on the top of visited, then the visited link will not turn blue if you hover.



### thought for clicked

*   changing the hsl for the similar color
*   changing the opacity
*   changing the background









