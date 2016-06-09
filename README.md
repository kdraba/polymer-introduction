# Polymer Introduction

## How to use this introduction

- start by running over this page
- checkout the latest branch and checkout its first commit in history, and follow the README.md of that commit

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
