# image

---

### image element

```html
<img src="img/garden" alt="garden">
```

`src` stands for source

`alt` stands for alternative text

>   alt text act as a description of the image and it appears when the image for some reason does not load 

<img src=".assets/image-20231128002109442.png" alt="image-20231128002109442" style="zoom:50%;" />

<font color='LimeGreen'>pretend the HTML5 Logo is the alt text</font>



### addtional attribute

```html
<img src="img/garden.jpg" alt="garden" title="garden in SuZhou" width="300" height="300">
```

`title` is not necessary *when you hover your mouse over the image, the title content will appear*

`width & height` is recommended now because <font color='OrangeRed'>cumulative layout shift</font>

>   give the browser an idea of how big your image is



### loading attribute

```html
<img src="img/garden.jpg" alt="garden" loading="lazy"
```

`loading` stands for the status of loading images

```html
loading="eager" <!-- eager is the default status for loading --> 
```

*   when the status is eager, your website automatically load all the images when you load the website
*   when the status is lazy, only when you scroll down to the spot where the images in will the web load the image



### figure

```html
<figure>
  <img src="img/garden.jpg">
  <figcaption>
  garden in the Suzhou
  </figcaption>
</figure>
```

in this way, the description of the image will appear underneath the image

>   you can put it under a image without the <img> attribute and it works



```html
<img src="img/garden.jpg" alt="garden">
<figure>
	<figcaption>
  An Example
    <code>&lt;h1&gt;Hello world!&lt;/h1&gt;
    </code>
  </figcaption>
</figure>
```

in this way, the "An Example" will appear under the image 

`code` it will print out the original code, be careful for the grammar of <h1> and </h1>



### image resource

>   file="21-of-the-best-placeholder-image-generators"

*   placeholder.com

it will generate a picture to temporary put there until you find the suitable picture

*   fill murray

provide a random picture of the actor fill murray



#### license for free use

*   unsplash.com
*   pexels.com
*   gratisography.com
*   pixabay.com



#### free image software

*to edit the size or the pixel of the image*

*   irfanview.com
*   canva.com
*   tinypng.com
*   