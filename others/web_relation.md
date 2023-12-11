# web relation

## client & server

```mermaid
graph LR
 pc -- https://... --> server  -- process --> html --> pc
```

| client       | funtion              | server        | function                        |
| ------------ | -------------------- | ------------- | ------------------------------- |
| browser      |                      | php           | read exist data and output html |
| mobile phone |                      | mysql         |                                 |
| html         | the page             | Ruby on Rails |                                 |
| css          | decoration           | Python        |                                 |
| javascript   | movement for the web | Java          |                                 |



## language execute order 

```mermaid
graph LR
pc --> browser-- request --> server --> a[php--read exist program]--pull data from mysql--> b[output html] --> browser
server -. run on the server.-> b
browser --html, css, javascript --> pc
browser -. run on local .-> pc
```

>   notice that html, css, javascript  run on the server