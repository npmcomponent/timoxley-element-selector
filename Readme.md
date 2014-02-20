*This repository is a mirror of the [component](http://component.io) module [timoxley/element-selector](http://github.com/timoxley/element-selector). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/timoxley-element-selector`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# Element Selector

  Select DOM elements with the mouse.

## Installation

```
$ component install timoxley/element-selector
```

## Example

```js
var ElementSelector = require('element-selector');
var elementSelector = ElementSelector();

```

[Demo](http://timoxley.github.com/element-selector/examples/)

## Options
  - [selector](#selector)
  - [selectEvent](#selectEvent)
  - [selectedClass](#selectedClass)
  - [highlightedClass](#highlightedClass)
  - [useDefaultStyles](#useDefaultStyles)

<a name="selector" />
### selector
Only trigger select/highlight events on elements matching this selector.
Defaults to `body *`.
```js
// Only trigger on paragraphs inside #content
var elementSelector = ElementSelector({
  selector: "#content p"
})
```

<a name="selectEvent" />
### selectEvent
Mouse event to trigger selection. Must be one of `click`, `dblclick`,
`mouseup` or `mousedown`. Defaults to `click`
```js
// Trigger on 'mousedown' instead of 'click'
var elementSelector = ElementSelector({
  selectEvent: "mousedown"
})
```

<a name="selectedClass" />
### selectedClass
```js
// elements will get class "editable" when they are highlighted
var elementSelector = ElementSelector({
  highlightedClass: "editable"
})
```

<a name="highlightedClass" />
### highlightedClass
```js
// elements will get class "glow" when they are highlighted
var elementSelector = ElementSelector({
  highlightedClass: "glow"
})
```

<a name="useDefaultStyles" />
### useDefaultStyles
Disable this if you wish to disable the default styles.
Adds `element-selector` class to `document.body` if `true`.
Defaults to `true`.

```js
// Disable default styles so you can
// use custom .selected and .highlighted css.
var elementSelector = ElementSelector({
  useDefaultStyles: false
})
```

## Events

Events are fired whenever an element's selected or highlighted status
changes. Two arguments are passed to the callback: the element that was highlighted
or selected, and the original mouse event that triggered the action (if
it exists). The second event argument is supplied if you wish to
prevent default actions or otherwise query the triggering event.

Events will be one of the following:

  - select
  - deselect
  - highlight
  - dehighlight


ElementSelector's event API is inherited from
[component/emitter](https://github.com/component/emitter).

### Example

```js

elementSelector.on('select', function(el, event) {
  event.preventDefault()
  console.log('element selected', el)
})

elementSelector.once('dehighlight', function(el) {
  console.log('element dehighlighted', el)
})

```

## API

  - [disable](#disable)
  - [enable](#enable)

<a name="disable" />
### disable()
Disables the elementSelector instance. No more events will be fired, other
than those to deselect/dehighlight the currently selected/highlighted
elements.

```
  elementSelector.disable()
```

<a name="enable" />
### enable()
Reenables a elementSelector instance.

```
  elementSelector.enable()
```

## Compatibility

  Only tested in Chrome. Pull request welcome if you get it working in IE.


## License

[MIT](http://opensource.org/licenses/mit-license.php)
