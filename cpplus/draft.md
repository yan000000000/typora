```mermaid
pie
	title why people stay at home
	"like_to_stay" : 60
	"too_cold" : 20
	"poor" : 5
	"do_nothing" : 10
	"same" : 5
```

```mermaid
graph LR
	A[start] --> B{is it?};;
	B -- Yes --> C[ok];
	C --> D[Rethink];
	D --> B;
	B -- No --> E[End]
```
