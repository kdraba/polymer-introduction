# Polymer Introduction

## How to use this introduction

- start by running over this page
- checkout the latest branch and checkout its first commit in history, then follow the README.md of that commit

## Trying to get some common objections out of the way

[Web Components](http://webcomponents.org/)? Oh no! Not another javascript frontend framework! - you might think.
Don't worry! Web Components are not another framework! Web Components are not a framework at all! Just think of them as a concept or a standardized pattern for using some great new core platform features of the browser.

'Yeah - if you say so ...', your inner voice might reply, '... but ...', and thats a very long '... buuuuuuut ...': '[Polymer](https://www.polymer-project.org/1.0/) is a framework or is it not?' So back where we started, just shout it out loud: 'Polymer? Oh no! Not another javascript frontend framework!'.

You got me there. Polymer is not a core feature of the browser platform and it IS code and not a concept or usage pattern! - But wait. Is [the ajax part of jquery](http://api.jquery.com/jquery.ajax/) a framework? Is [momentjs](http://momentjs.com/) a framework? To me, they are not. To me, these are just libraries that make developer live much easier, when it comes to ajax requests and dates. To me, the same is true for Polymer. Polymer makes my life a lot easier, when it comes to writing custom elments. Thank you for that!

Polymer has an ever growing ecosystem. That's not a bad thing. But that's not what this introduction is about. This introduction is about the core library and not about the frameworks you can build on top of it. There are some aspects of the core library that i think are framework-ish, e.g. some implications on its use of [bower](https://bower.io/) and [HTML imports](http://w3c.github.io/webcomponents/spec/imports/), but these aspects are evolving and i still hope for the best.

## Elements of an HTML page

```html
<!doctype html>
<html>
  <head></head>
  <body>
    <input value="2016-06-10" type="date" onchange="document.querySelector('#user_text').textContent = this.value">
    <div>Dein Datum: <span id="user_text" style="font-weight: bold">2016-06-10</span></div>
  </body>
</html>
```

- HTML/DOM - hierarchical structure
- elements - semantic, look and feel, dynamic
- CSS/style - look and feel
- Javascript - dynamic, logic
- Events - dynamic

## Web Components

- [Web Components website](http://webcomponents.org/)

Web Components are based on emerging web standards 

- [custom elements](http://w3c.github.io/webcomponents/spec/custom/)
- [HTML imports](http://w3c.github.io/webcomponents/spec/imports/)
- [template element](https://html.spec.whatwg.org/multipage/scripting.html#the-template-element)
- [shadow DOM](http://w3c.github.io/webcomponents/spec/shadow/)

## Polymer

- [Polymer Webseite](https://www.polymer-project.org/1.0/)

In its core its an implementation of Web Components

- [Polymer library](https://www.polymer-project.org/1.0/docs/devguide/feature-overview)
- [Polymer elements](https://elements.polymer-project.org/)

Good starting points:

- [Polymer Summit 2015](https://www.youtube.com/playlist?list=PLNYkxOF6rcICdISJclfQhj2S8QZGjXV8J) especially [Thinking in Polymer](https://www.youtube.com/watch?v=ZDjiUmx51y8&index=3&list=PLNYkxOF6rcICdISJclfQhj2S8QZGjXV8J)

## Getting set up and started

- git ([Git for Windows](https://git-for-windows.github.io/))
- [nodejs](https://nodejs.org/en/) ([latest release](https://nodejs.org/en/download/current/))

- [Git Extensions](https://gitextensions.github.io/) ([latest release](https://github.com/gitextensions/gitextensions/releases/latest))
- [Brackets](http://brackets.io/) ([latest release](https://github.com/adobe/brackets/releases/latest))

## Polymer Starter Kit and Polymer CLI

- [Polymer Starter Kit Github](https://github.com/PolymerElements/polymer-starter-kit)
- [Polymer CLI](https://www.polymer-project.org/1.0/docs/tools/polymer-cli)
