# UMD (Universal Module Definition) en CoffeeScript

[UMD](https://github.com/umdjs/umd) permet de définir des modules javascript compatibles avec à peu près tout (node.js, browser, commonjs, etc...)

Voici une implémentation coffeescript du pattern le plus utilisé.

```coffeescript
do (
    root = this,
    factory = ->
        myModule = {}

        # define module here, and returns it

        myModule
) ->
    if typeof define is "function" and define.amd
        define [], factory
    else if typeof exports is "object"
        module.exports = factory()
    else
        root.myModule = factory()
    return
```
