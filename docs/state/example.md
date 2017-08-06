# An example: To-Do list

---
In the default project that's created when you run `reactql new`, you'll see a Redux counter working out-the-box. You can click the button [http://localhost:8080](http://localhost:8080), and the number increments by one.

Despite this being a very trivial example, this is Redux at work. Multiple components could 'listen' to the current count, and update their UI based on, say, hitting a specific number. Or they could fire an action that would modify the state further. This simple example is surprisingly difficult to implement across an application with many React components, without a library like Redux to centrally manage 'state'.

For the rest of this section, I'm going to explain what's happening under the hood with another example: A to-do list.

I encourage you to review the [Redux documentation](http://redux.js.org/) too, to get familiar with how Redux works. Rather than repeating concepts, I'll leave that to the library's author to tackle and instead focus on code.
