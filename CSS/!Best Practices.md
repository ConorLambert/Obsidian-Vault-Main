#### CSS Declarations Order
- Multiple selector declarations should be declared before individual selector declarations:

```html
h1, p {
	margin-top: 0;
}

h1 {
	font-size: 24px;
}

p {
	font-size: 18px;
}
```