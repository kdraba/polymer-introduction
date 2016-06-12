# Talk

## Current Step

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

## Previous Steps

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