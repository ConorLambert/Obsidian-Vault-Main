When multiple threads could potentially create multiple instances of our singleton class, it violates the fundamental principle of the Singleton pattern — one and only one instance!

```
public sealed class ThreadSafeSingleton
{
    private static ThreadSafeSingleton instance = null;
    private static readonly object lockCheck = new object();

	private ThreadSafeSingleton(){}
	
	public static ThreadSafeSingleton Instance
	{
		get
		{
			if (instance == null)
			{
				lock(lockCheck)
				{
					if (instance == null)
					{
						instance = new ThreadSafeSingleton();
					}
				}
			}
			return instance;
		}
	}
}
```

In this simple yet effective code example, the ‘lock’ keyword is like the bouncer at the entrance of a club, admitting one person in (or one thread into the block of code) at a time. 
Even when multiple threads try to access it at once, only one gets through making sure the instance, once created, is the one and only.

#### Why Double Check?
- Lock operations are costly
- The instance won't be null after the first few times its checked. I say first few times because multiple threads might be accessing it simultaneously for the first time.