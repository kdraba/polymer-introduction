# Talk

## Current Step

### Formatting the date

We are using [Moment.js](http://momentjs.com/) to format the date. First, we need to install the library using [bower](https://bower.io/).

```shell
node_modules/.bin/bower install --save momentjs
```
In our [app/index.html](./app/index.html) file we include the installed library and update the binding to use a function for formatting the date `<span>[[dateFormat(comment.date)]]</span>`. This function, and therefor the binding, will be updated each time the date attribute of the comment changes, or more specifically the date changes and a change event is fired for the path.

## Previous Steps

### Adding a date to our comment

Next we restructure our comment to include a date in additon to the message. In [app/scripts/app.js](./app/scripts/app.js) we simply change the structure of our items in the initial comment list and of the new comment added to the array.

In [app/index.html](./app/index.html) we now use path expression in our bindings to accommodate the structural change.

The added date takes up a lot of space in our view, because it is very verbose. We are going to fix that in our next commit.

### Deleting comments

To delete a comment we need a button inside our template for each individual comment. Just like with the add button we hook this button up with a `on-tap` handler. We do all this in our [app/index.html](./app/index.html).

The implementation of our handler is a little bit more interesting, because we need to map our event to the comment we want to remove from the list. As you might expect, its quiet easy. An event fired from an element within a `dom-repeat`-template simply provides us the item and the index the element was rendered for in its `model` property ([handling events in dom-repeat](https://www.polymer-project.org/1.0/docs/devguide/templates#handling-events)).

In the next commit we will change the type of our comment from a flat string to an object with a date and a message.

### Adding new comments - the Polymer way

The Polymer binding system is event based, i.e. each element changing a value is firing an event designating the change of the value. Other elements may be listening for these events and reacting to them by updating their own values.

This means that changing the value itself, as we did in our first approach with adding new comments by pushing them directly on to the array, is not enough. We also need to fire some events to inform listeners. There are some Polymer functions for that available on each Polymer element, i.e. `notifyPath` and `notifySplices` but there are also some convenience functions like `set`, `push` and `splice` (for arrays have a look at [array-mutation](https://www.polymer-project.org/1.0/docs/devguide/properties#array-mutation)).

We could have used the `push` convenience method but we want the new comment to be at the top of the view, i.e. we want it to be the first in the list so we use `splice` instead. And that we do in [app/scripts/app.js](./app/scripts/app.js).

Now everything is working fine. We let Polymer do the work and allow it to simply add a single element to the list view instead of forcing it to rerender the complete list.

Being able to add new comments is great, but we should also be able to delete them, just in case. This we do in the next commit.

### Adding new comments - second approach

We know that our binding is working somehow, because we would not see our inital commits if this were not the case.
Initially we did assign the complete list, so lets try that approach for adding a new comment to our list.
A new assignment as in [app/scripts/app.js](./app/scripts/app.js) should do the trick.

Take a look at our [app](http://localhost:5000/) - it is working. But lets reconsider. What about large lists? Do we really want to create a new copy of the list for a simple change? What about rendering - does the browser have to rerender all the elements in the list simply because of on new added comment?

Of course not, i would not ask otherwise - so have a look at the next commit where we are doing things in the Polymer way.

### Adding new comments - a first approach

In order to add comments we need to extend our ui. We will extend it with a simple input field to insert a new comment and a simple _send_ button to add the comment to our list. Of course, we are using web components for both the input field and the button.

The [paper-input](https://elements.polymer-project.org/elements/paper-input) element will provide us with a beautiful input element and the [paper-button](https://elements.polymer-project.org/elements/paper-button) element with a beautiful button. To use the two new elements we need to import them in our [app/elements/elements.html](./app/elements/elements.html). In our [app/elements/elements.html](./app/elements/elements.html) we import all the elements we need directly in our [app/index.html](./app/index.html). Imports that we are using only in our own custom elements should be importet there. We are using `<link rel="import" src="..">` here, i.e. the HTML import feature which will handle for us multiple imports of the same file, hence we do not need a centralized file for all imports and each element should declare all the imports it requires itself and no more than that.

We use the two elements in our [app/index.html](./app/index.html) file right above our list of comments. The things happening here are obvious, which is great because that is one of the promises of the declarative approach taken by web components.

We are binding the value of the `paper-input` to `newComment`. This time we are using curly braces to allow a bidirectional binding, i.e. a binding from host to child as well as from child to host. Hence we may provide the `paper-input` child with an inital value and more importantly the `paper-input` child element may write its value into the `newComment` variable of our `#app` host element.

To trigger the addition of the new comment we add an `on-tap` handler to the input. This handler is in the scope of our `#app` element, hence we register the required function there in our [app/index.html](./app/index.html). In the Polymer world you may just want to use `on-tap` instead of `on-click` everywhere, because there is nothing to loose but only gain in that.

With our UI set up take a look at our app at [localhost](http://localhost:5000/). Is it not beautiful? I do not think so! The input field and button are nice, thanks to the material design, but the rest ... ok lets be honest with you from the start ... that is as beautiful as it will get in the course of this introduction ... sorry.

Now lets think about the logic to add the new comment to our list of comments. With our comment list in place this seems straight forward. Simply use the event handler to push the new comment on to the array as done in [app/scripts/app.js](./app/scripts/app.js).

But wait its not working, isn't it? Add as many comments as you like they are not shown in the comment list. Lets have a closer look. Open the development console of your browser and type: 

```javascript
document.querySelector('#app').comments
```

There they are, all the missing comments you entered previously are in the array but not shown in the view. Obviously our event handler is working just fine, but the binding is not. We must have done something wrong and its not your fault but mine for leading you astray by intent.

Lets see if we get better luck with our next commit.

### A list of comment items

It is time to do something a bit more interesting. Lets use Polymer to display a simple list of comments.
Our comments are just a simple list of Strings for now. You can see them in [app/scripts/app.js](./app/scripts/app.js).

We register our list of comments as a new property of the `#app` element. To understand how our list is displayed, we need to have a look at the [app/index.html](./app/index.html) file.

First thing to point out is that the element with id `app` is an HTML `template` element with a special `is="dom-bind"` attribute. This attribute and its value are telling Polymer that we want it to bind its content (see: [dom-bind](https://www.polymer-project.org/1.0/docs/devguide/templates#dom-bind)). In general binding is done automatically for our custom elements. But we do not have a custom element here - we will create some later on. So we just tell Polymer to bind this template right away without the need for definint a custom element.

Next thing to point out is the `template` element inside our `#app` element. As you might have guessed already this is what defines what our comments in the list look like. Each of our comments is rendered into the view by stamping the template for each of our items, i.e. each of our comments, that is what `template is="dom-repeat"` is for (see [dom-repeat](https://www.polymer-project.org/1.0/docs/devguide/templates#dom-repeat)).

The binding expression `items="[[comments]]"` references the `comments` property at the `#app` element which we did set up in [app/scripts/app.js](./app/scripts/app.js) before. The attribute `as="comment"` simply tells the binding that we want to be able to reference the individual item inside our template by `comment` which we do when simply stamping the text of each comment in `<div>[[comment]]</div>`.

Do you wonder what the square brackets are for? They mark this binding as a top-down binding, i.e. a binding from host to child only. This will become clearer further into the introduction. (If you feel urgent have a look at [property-binding](https://www.polymer-project.org/1.0/docs/devguide/data-binding#property-binding))

Lets peek ahead a bit. Someone asked me: "If Polymer is about custom elements, why not use a custom `dom-repeat` element instead of the `template` element with an `is="dom-repeat` attribute?" My reasoning is: a custom element has to be interpreted by the browser and a template has not. What do i mean by that? If you wrap a `template` in a custom element just for the sake of the custom element, the browser has to process that element just to get eventually to a wrapped `template` element with which the browser would still do nothing.
Feel free to correct me here - i am still learning too.

Now that we got a basic list of comments in place, lets go to the next commit where we start working on a feature to add new comments to our list.

### Our hello-world element - the Polymer way

### Going back to html by using html template for our hello-world element

[MDN HTML Template](https://developer.mozilla.org/de/docs/Web/HTML/Element/template)

### Using html import to import our hello-world element

[MDN HTML Imports](https://developer.mozilla.org/en-US/docs/Web/Web_Components/HTML_Imports)

### Making hello-world a custom element

[MDN Custom Elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Custom_Elements)

### Making our hello-world world reusable

### Creating a hello-world component without web components api

### Going back to the roots

The Polymer Starter Kit is great. But I prefer learning by doing small steps and understanding changes line by line.
Hence i removed all the great content from the Polymer Startet Kit leaving us with the dreaded blank page.

Thats it for this step. Continue to the next commit ... yes you could really have skipped this one.

### Start

Welcome to my Polymer introduction and thank your for your interest!

To follow this introduction you need to follow the git commits in this repository in their historical order. Simply check out the first commit in repository history and follow me along by reading the [TALK.md](./TALK.md) file of each revision.

I suggest you use a tool like [Git Extensions](https://gitextensions.github.io/) ([latest release](https://github.com/gitextensions/gitextensions/releases/latest)) to follow the trail of commits.

The current project state your looking at is a plain [Polymer Development Kit 1.3.0 release](https://github.com/PolymerElements/polymer-starter-kit/releases/tag/v1.3.0) with some minor tweaks, e.g. a changed project name in [bower.json](./bower.json) and this new [README.md](./README.md) file added.

First install or update the dependencies and serve the Polymer Starter Kit, then have a look around.

Install or update dependencies:

```shell
npm install
npm install --save-dev bower
node_modules/.bin/bower install
```

Serve the Polymer Starter Kit:

```shell
node_modules/.bin/gulp serve
```

Take a look at the app running on [localhost](http://localhost:5000/) and at the [app/index.html](./app/index.html) file. Just hurry - because we are going to make it all go away when switching to our next commit :wink:.

Did you spot all those pretty material design custom HTML elements in the [app/index.html](./app/index.html) file? Could you map those element to their beautiful appearance int the [app](http://localhost:5000/)? - Sure you did, or did you not? Anyway, just stay with me as we use and build some simple elements in this introduction to shed some light basic Polymer principles.

In case you want to leave the introduction right away and experiment with the Polymer Starter Kit you can find informations in their original [ORIGINAL_README.md](./ORIGINAL_README.md).

Now it is time to switch to the next commit in repository history.