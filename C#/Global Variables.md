- In C# you cannot define true global variables (in the sense that a variable can't not belong to any class).
- This being said, the simplest approach that I know to mimic this feature consists in using a static class and fields.