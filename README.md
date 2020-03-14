```js
let el = (() => {
    let elements = {};
    elements.id = {};
    elements.class = {};
    elements.tagName = {};
    for (let element of document.querySelectorAll('*')) {
        if (element.id) {
            elements.id[element.id] = element;
        }
        if (element.className && typeof element.className === 'string') {
            element.className.split(' ').forEach(function (class_) {
                if (!elements.class[class_]) { elements.class[class_] = []; }
                elements.class[class_].push(element);
            });
        }
        let tagName = element.tagName.toLowerCase();
        if (!elements.tagName[tagName]) { elements.tagName[tagName] = []; }
        elements.tagName[tagName].push(element);
    }
    return elements;
})();

// el.tagName.div

```
