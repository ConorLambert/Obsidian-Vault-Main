#### Important
- Lazy initialization is thread-safe, ==but it doesn't protect the object after creation==. 
- You must lock the object before accessing it, unless the type is thread safe.