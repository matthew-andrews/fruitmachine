![fm logo](artwork/logo.jpg)

A lightweight modular layout engine for client and server. Currently powering the award winning FT Web App. FruitMachine was designed to construct nested view layouts from strictly modular components.

```js
// Define a module
var Apple = FruitMachine.define({
  module: 'apple',
  template: function(){ return 'hello' }
});

// Create an instance
var apple = new Apple();

// Render & inject into DOM
apple.render().inject(document.body);

apple.el.outerHTML;
//=> <div class="apple">hello</div>
```

## Contents

- [Introduction](docs/introduction.md)
- [Getting started](docs/getting-started.md)
- [Defining modules](docs/defining-modules.md)
- [Instantiation](docs/instantiation.md)
- [Queries](docs/queries.md)
- [Templates](docs/templates.md)
- [Template markup](docs/template-markup.md)
- [El](docs/view-el.md)
- [Helpers](docs/helpers.md)
- [DOM injection](docs/dom-injection.md)
- [Extending](docs/extending.md)





## Why not Backbone?

- No deps
- Can be retrofitted into a parts of a legacy system, it's not a religion
- Serverside has been considered from the start
- It doesn't care how you manage your data
- Modules are designed to be reused in multiple contexts, you create layouts, not fixed views
- A little more structured than Backbone

## Author

- **Wilson Page** - [@wilsonpage](http://github.com/wilsonpage)

## Contributors

- **Wilson Page** - [@wilsonpage](http://github.com/wilsonpage)
- **Matt Andrews** - [@matthew-andrews](http://github.com/matthew-andrews)


## License
Copyright (c) 2012 Wilson Page
Licensed under the MIT license.