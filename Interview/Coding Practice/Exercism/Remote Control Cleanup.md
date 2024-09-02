[Source](https://exercism.org/tracks/csharp/exercises/remote-control-cleanup)

# Lessons Learned
- You can't create a public property of a private type.
	- If class `Telemetry` is private, then you can't have a public property of type `Telemetry`.
	- The `Telemetry` class must be public to work in this case
- A workaround here is to create a public interface that the private class implements and then use the public interface as the public properties type.