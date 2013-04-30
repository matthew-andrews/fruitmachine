## Getting started

Let's start with a very simple example to demonstrate how to work with FruitMachine.

#### Define some modules

```js
var Apple = FruitMachine.define({
  module: 'apple',
  template: function(){ return 'I am an apple'; } /* 1 */
});

var Layout = FruitMachine.define({
  module: 'layout',
  template: function(data){ return data.child1; } /* 1 */
});
```

1. *For simplicity we are using plain functions for templating. These can be switched for more advanced templating functions (eg. Hogan/Mustache).*

#### Assemble a view

```js
var layout = new Layout();
var apple = new Apple({ id: 'child1' }); /* 1 */

layout.add(apple); /* 2 */
```

1. *Notice how we give this instance of apple an id. This is the module's identifier within this view, it should be unique. We use this id to print the child into the parent's template.*
2. *Here we add the apple view module as a child to the layout view module.*

#### Rendering the view

```js
layout.render(); /* 1 */
```

1. *At this point `layout.el` will be populated with a real DOM node*

#### Injecting the view into the DOM

```js
layout.inject(document.body); /* 1 */
document.body.innerHTML; //=> <div class="layout" id="fmid-195834-a"><div class="apple" id="fmid-243252-a">I am an apple</div></div>
```



### Lazy Views

FruitMachine was written for flexibility so there is usually more than one way to do something. In this case the above code could also be written like this:

```js
var Apple = FruitMachine.define({
  module: 'apple',
  template: function(){ return 'I am an apple' } /* 1 */
});

var Layout = FruitMachine.define({
  module: 'layout',
  template: function(data){ return data.child1 } /* 1 */
});
```


```js
var layout = new FruitMachine.View({
  module: 'layout', /* 1 */
  children: [
    {
      module: 'apple', /* 1 */
      id: 'child1'
    }
  ]
});

layout
  .render()
  .inject(document.body);
```

1. *Because we have defined modules under these names, FruitMachine is able to instantiate them internally.*

It is useful to be able to assemble views in this way as it means that you can predefine your layouts as simple JSON, letting FruitMachine do the hard work. For some parts of your application this may not be preferable. In the FT Web App we use a combination of the two techniques. Sometimes it's nicer to have more control :)