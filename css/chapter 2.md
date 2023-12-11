# lesson 2 selectors

---

>   selectors select all the element of that type

### body

*   only one body element for one html file



### class

```css
.gray{ 
  color: gray;
}
```

`.gray` stands for class in this case

change paragraph with gray class to gray

*   more specific
*   most common type of selector



### id

```css
#second {
  font-style: italic;
}
```

*   most specific
*   not good idea, rare or never

*   try to keep them out of the css



### multiply rule

```css
h1, h2{
  color: blue;
}
```

in this way, it works h1 or h2

```css
h1 h2{
  color: blue;
}
```

not always work

it equal to search for the h2 in the h1



#### example for one in other

```css
p span{
  text-transform: uppercase;
  background-color: gold;
}
```

it will search all the span in the paragraph



### universal selector

```css
* {
  
}
```

this is a selector select all the element



### inheritance

*   using universal selector are not inheriting, it select all the element
*   some element do not inherited e.g. border, font, form element

*   most do , e.g. body, html, main,



### important

```css
!important
```

override all the code 

don't use it for beginner, rude the code