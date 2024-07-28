### Illegal
- Indexers are not allowed in static classes
- Indexers require a reference to `this`. Since Static Classes aren’t instantiated - they don’t have `this`.

### Singleton with an Indexer
- The next best thing is to create a Singleton class (check out this [article](https://buildplease.com/pages/singleton-indexer/))