# window.requestIdleCallback()

Some websites have a lot of scripts to execute. Executing bunch of scripts on a page can interrupt the user.

For example,

Assume user is scrolling the page and you are sending analytics data in the background, your web app can become unresponsive that can cause poor user experience.

We can delay the lower priority tasks/scripts that does not need to happen immediately until the browser isn’t working on something more important.

Good News!

requestIdleCallback will schedule work when there is free time at the end of a frame, or when the user is inactive. This means that there’s an opportunity to do your work without getting in the user’s way. This effectively allows us to register a callback function to be executed when the browser is idle.Instead of us trying to calculate when to run certain tasks, we can simply tell the browser to run them whenever it gets a chance.

requestIdleCallback(callback[, options]);

- first argument is the callback function that we want executed when the browser is idle
- second argument is an object we can pass in additional options.

eg: requestIdleCallback(doLowPriorityTask, { timeout: 3000 })

timeout allows us to specify the maximum amount of time we’re willing to wait before the browser must execute the callback.

This would add a call to my doLowPriorityTask() function into the queue of things to do whenever the browser is idle. But if that doesn’t happen in the next 3 seconds, the function would be called regardless.

Canceling the Callback
In those situations where you need to cancel a previously scheduled callback, you can do so by using:

cancelIdleCallback(handle);
