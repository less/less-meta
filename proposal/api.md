## Less API 3.0 Proposed Changes
### Intro
The Less API and plugin architecture suffers from having too large a scope. Right now everything everything is customizable in the same way that you can customize any part of Linux. That is, the fact that you can in theory doesn't mean an average person can in actuality.

### Goals of API changes
* Reduce the number of exposed methods to what's really intended to be extendable
* Examine the AST and see if # of nodes and node methods can be simplified, for example:
* Fix node methods to be evaluatable without passing in environment / context / frames whatever. (e.g. Ruleset.toCSS() or Ruleset.eval() working without parameters)
* Make the ```@plugin``` (Plugin type A) the primary or preferred plugin method, and expand ```@plugin``` to support custom @-rules.
* Clarify that plugin type B (command-line plugins) is for global / Less environment. In other words, a good example for type A would be adding a custom function. For type B, it would be adding a custom file handler. But type B should be separated into "advanced usage".

### More assistance to developers
* Documentation, Documentation, Documentation
* Publish "best practice" page for developers on plugin development
* Create a Less plugin bootstrap repo that's clonable as a starting point
* Evangelism - talk directly to Less library authors about how plugins could solve problems.

### List of API changes
TBA
