# DOM Observer

A library for easily tracking DOM mutations.

You can set handlers for when:

* a node is added to the DOM
* a node is removed from the DOM
* a node's attributes are changed

Furthermore, you can only observe mutations on a specific node's tree.
The attributes for which to observe changes can be filtered.

## How do I use it?

You create a `DOMObserver` and pass it the handlers you want. A handler can
take the corresponding DOM node (inserted/removed/changed) as
parameter.

```javascript
var observer = new DOMObserver(document.querySelector("#my-node"), {
    addedNodeHandler: function (addedNode) {
        console.log("Following node was added: " + addedNode);
    },
    attributeFilter: ["data-awesome"],
    mutationHandler: function (changedNode) {
        console.log("Following node's data-awesome attribute was changed: " + changedNode);
    }
});
```


When you are done checking for mutations, you can easily stop the observer.

```javascript
observer.shutdown();
```

## Browser support

[MutationObserver](https://developer.mozilla.org/en/docs/Web/API/MutationObserver)
is used for browsers that [support](http://caniuse.com/mutationobserver) it.
[Mutation events](https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Mutation_events)
are used as a fallback.