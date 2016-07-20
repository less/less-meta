## Plugins

Less.js plugins allow you to extend the functionality of the compiler and add available functions to your code.

### Installing plugins

Plugins can be local relative to your `.less` files, or installed via NPM when using Less in Node.js.

By convention, Less plugins often start with `less-plugin-`, although that's not required. For example, for the clean-css plugin, you would install using the following:
```
npm install less-plugin-clean-css
```
In a browser, your plugin can be distributed as a single file along with your other web assets.

### Using a plugin

The easiest way to use a plugin is to import it into your `.less` code.
```less
@plugin "clean-css";
@import "mylibrary";

// Other styles
```
This method works either in the browser or in Node.js, just like your other imports. In Node, your `node_modules/` folder is searched for the `less-plugin-clean-css` or `clean-css` module. Then, the local folder is searched for `clean-css.js` and `less-plugin-clean-css.js`. In the browser, Less will only search locally.

You can also use a local directory reference (`./`) to limit searches to local in either environment. For example, if you have a root file called `styles.less` that has:
```less
@plugin "./my-plugin";
```
Less will only look for `my-plugin.js` in the same folder as `styles.less`.

For Advanced Usage of installing plugins, see the Plugin Advanced Usage page.

### For Plugin Authors

Plugin files / modules return an object with a simple signature. All of the functions are optional.

```js
/* can also use module.exports = {} */
return {   
  /* install() is run once. See the API for paramaters
   * 
   * @param less - Main less object
   * @param pluginManager - Allows you to add visitors, file managers, and post processors
   * @param functionRegistry - Can add functions for reference in your .less files  */
  install: function(less, pluginManager, functionRegistry) {},
  
  /* Options are set with @plugin (argumentString) "my-plugin" from .less files, 
   * or lessc --my-plugin=argumentString on the command line.  */
  setOptions: function(argumentString) {},
  
  /* Gives information about this plugin in lessc */
  printUsage: function() {},
  
  /* minimum Less.js version required for this plugin */
  minVersion: [3, 0, 0]
}
```

## Less.js API

### The `less` Object

The `less` object is the entry point for methods and objects to work with the Less.js compiler, and is available with the `require("less")` method in Node or available as a global in the browser (`window.less`).

### Less Nodes

#### `less.AtRule`

#### `less.Call`

#### `less.Declaration`

#### `less.DetachedRuleset`

#### `less.Mixin`

#### `less.MixinCall`

#### `less.Ruleset`

#### `less.RulesetCall`

### Plugin Manager

### Function Registry
