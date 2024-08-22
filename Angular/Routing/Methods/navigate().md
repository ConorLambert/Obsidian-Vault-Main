![[Pasted image 20240724162522.png|300]]

#### relativeTo
- ==Defaults to absolute routes unless we use the `relativeTo` property==
- The `relativeTo` property will start the URL navigation at the route defined (which is normally the `activatedRoute`).
- For example, if the `activatedRoute` is `localhost:4200/home` and the destination is `shop` then the new route will be `localhost:4200/home/shop`.
- The above point is important because if we use `relativeTo`, it is likely that we need to prepend the route parameter with `../` like so:

```typescript
this.router.navigate([`../shop`], {
	relativeTo: this.activatedRoute,
});
```

- This is because `localhost:4200/home/shop` is likely the wrong route, we need to navigate to `localhost:4200/shop` instead due to using the `activatedRoute` property.
