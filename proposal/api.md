## Less API
For the last item above, the Less API and plugin architecture suffers from having too large a scope.
Right now everything everything is customizable in the same way that you can customize any part of Linux.
That is, the fact that you can in theory doesn't mean an average person can in actuality.

Even though Less JavaScript plugins have been around much longer than PostCSS's, with a theoretical "greater capability",
PostCSS's plugins growth has been rapid, I'd say for a number of reasons, including:
* The API is _extremely_ limited. There are a total of 4 main node types. (Less has 28 node types, by the looks of things.) And the methods for those nodes are simple and consistent. (Many of Less's methods on nodes are not even directly callable without having knowledge of contexts and frames, making them largely unusable.)
* PostCSS's API is well-documented. (Less's API is largely undocumented.)
* PostCSS has "best practices" and guidelines for plugin development.
* PostCSS has under its org "starter repos" for plugins, which include tests (and instructions for setting up those tests) that the plugin must pass.

Less.js doesn't need to be like PostCSS (or at the extreme suggestion of some users, ditch any plugin features and just adopt PostCSS), but PostCSS is an example of successful plugin architecture, so it's worth looking at.

### Keeping things simple
I think we should:
1. Look at what parts of Less have been extended by plugins, and consider limiting the API around those.
2. Fix node methods to be evaluatable without passing in environment / context / frames whatever. (e.g. Ruleset.toCSS() or Ruleset.eval() working without parameters)
3. Document said API methods, which should be easier to accomplish with a limited set.

I also think that the ```@plugin``` syntax could be more successful than the "installable" plugins, because it's easier to use (and more limited, which is actually better), so it would make sense to make that more of the focus of the "plugin" feature.
