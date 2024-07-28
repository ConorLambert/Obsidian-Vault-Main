- What to do when none of the routes match
- User enters URL incorrectly or has an expired link.
- Wildcard route should the very last route.

```typescript
{ 
	path: '**', 
	pathMatch: 'full', 
	redirectTo: '/customers' 
}
```