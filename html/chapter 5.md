# lesson 5 -- hyper text

---



### absolute reference

```html
<a href="www.yanlin000yuru.xyz">my blog</a>
```

><font color='OrangeRed'>my blog</font>

this is a simple reference for an absolute website



### relative reference

```html
<a href="kyoto.jpg">photo</a>
```

>   <font color='OrangeRed'>photo</font>

you can simply type the name if the file is in the same directory with the website



### internal reference

turn to position in the page

```html
<nav> 
  <p>
    <a href="#code1">page1</a> //hypertext page1
  </p>
  <p>
    <a href="#code2">page2</a> //hypertext page2
  </p>
  
</nav>

<section id="code1">

</section>

<section id="code2">

</section>
```

>page1
>
>page2

`<nav>` stands for navigate

`#code1` stands for the id of the section <font color='OrangeRed'># is necessary</font>

 by clicking the page1 and page2, the webpage will redirect to the section where its section id match the one in the linkch



##### if you want to link to the section in another file

```html
<a href="home.html#code1">About LTS</a>
```



### link text rule

*   avoid printing the full web address to the page

>   <u>www.google.com</u> (don't printing the link like this)

*   avoid "links to" phrase. we all know it is a link

>   this is a link to <u>profile</u> (no use at all)

*   keep your link text short exact topic

><u>information about me</u> --> <u>about me</u>

*   no links that say "click here" it provides no meaning

>to learn more about me, <u>click here</u> (no good for reader, and confusing)



### download link

```html
<a href="kyoto.png" download> photo </a>
```

>   <u>photo</u>(click and the browser will download)



### email link

```html
<a href="mailto:random@email.com"> my email address </a>
```

>   <u>my email address</u> (when you click it will open the default mail editor to write to this email)
>
>   a thing of past, cause safety problem



### telephone number

```html
<a href="tel:+1234567890">my phone number</a>
```

>   <u>my phone number</u> when you click it it will turn to the dialer



### target? link

```html
<a href="https://www.google.com/" target="_blank">Google</a>
```

>   <u>Google</u>  (by clicking on it, you will open a new google tab)



### root link

```html
<a href="/">Back to home</a>
```

><u>Back to home</u> (By clicking the link, you will turn to the default, which is your ip/ with no other , defaultly is index.html)ode
