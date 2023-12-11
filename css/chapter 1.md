# lesson 1 start

### 3 ways to use css

#### link from the external file

```html
<link rel="stylesheet" href="css/style.css">
```

```css
p {
  font-size:64px;
  color:purple;
}
```

<font color='OrangeRed'>most common</font>

#### write in the header file

```css
<style>
p {
  	color: limegreen;
}
```



#### inline css

```html
<p style="color:blue">i'm learning CSS! </p>
```

<font color='OrangeRed'>super not recommend</font>

### priority

external and internal css file have no priority difference, it varies for the order of the configuration



### anatomy of a CSS ruleset

```css
p {
  color: red;
}
```

`p` stands for selector: it defines the elements to be styled

`color` stands for the property

`red` stands for the property value

`color: red` stands for the declaration



### reminder

*   css use American English e.g.(color instead of colour)

*   css don't abort because of the issue, they just skip the code

*   go to W3C to check for error
*   working waterfall, running from the top to the button, the rule read last will be executed

*   specificity go first than the order, it follow the most specific

*   you can inspect your code if you can't find your style bug