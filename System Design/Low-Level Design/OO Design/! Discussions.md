[What is the Best way to learn Object Oriented Design ?](https://www.reddit.com/r/learnprogramming/comments/1co7tk3/what_is_the_best_way_to_learn_object_oriented/)
- Continue to build software and actively reflect on the design you use.
- Get involved in Open Source and/or look at existing code bases.
- Read books and watch videos but *though don't force it where it doesn't fit*.
- Ask yourself, did things becomes more or less complex by using some pattern or design? Why? If it did, might we do better by not using it? What could the alternative be?
- If you want feedback on your design: *Write automated tests. If you find it difficult to write short and expressive tests, then you most likely have a bad design.*
- I might have an overall vision that I want to create, but I break it down into smaller parts.
	- *It is all about breaking down the work into tasks to the point that you can start working on them.*
- You should know enough about the requirements to the point that you know what problem to solve - but you don't need to know the exact implementation or anything like that.
	- You should have an overarching architecture in terms of technologies you want to be using, what kind of system architecture you're going to be using, how different systems within the solution connect, etc. The high level stuff.
- A piece of advice I got from a professor years ago - "Use functions that don't exist"
	- Instead of thinking about all the objects you'll need, designing them out, etc. - start by writing the code that will use those objects, before it's even created. Just write whatever feels the most natural and most in-place.
	- Then from here, I would go define each function that is used in this function but not already defined.


