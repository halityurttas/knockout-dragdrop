# knockout-dragdrop

A drag and drop binding for Knockout.

---

## IMPORTANT (The aim of change)

This fork changed drop event model parameter to event parameter. Get model from event.data property if you access it so we access target element from event.element property. Please take notice!

We get target element and we could know to which model from attribute like data-model that you see sample below

---

[Click here to see an example](http://one-com.github.io/knockout-dragdrop/examples/)

## Install

### NPM

`npm install knockout-dragdrop`

### Bower

`bower install knockout-dragdrop`

## Usage

Dragging between two lists:

```html
<h2>Drag from here</h2>
<ul data-bind="foreach: source">
    <li data-bind="text: $data, dragZone: { name: 'lists' }, attr: { 'data-model' : 'source' }"></li>
</ul>

<h2>Drop here</h2>
<ul data-bind="foreach: target, dropZone: { accepts: 'lists', drop: drop }, attr: { 'data-model' : 'target' }">
    <li data-bind="text: $data"></li>
</ul>
```

```js
var model = {
    source: ko.observableArray([
        'Declan',
        'Tessa',
        'Claire',
        'Violet',
        'Alice',
        'Mia',
        'Camille',
        'Aiden'
    ]),
    target: ko.observableArray(),
    drop: function (data, event) {
        event.data.source.remove(data);
        event.data.target.push(data);
        // you found target element in event.element and so wich model from get the attribute or etc 
    }
};
ko.applyBindings(model);
```

## Running the example locally

Run the following command:

```
npm install && bower install && serve
```

and open [http://localhost:3000](http://localhost:3000) in your browser.

## License

Knockout.dragdrop is licensed under a standard 3-clause BSD license -- see the `LICENSE`-file for details.
