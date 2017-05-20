# Polymer 2.0 API Upgrade CheatSheet

**Before**
```js
Polymer.dom(this.root)
```

**After**
```js
this.shadowRoot
```

---

**Before**
```js
Polymer.dom(event).localTarget
```

**After**
```js
event.target
```

---

**Before**
```js
Polymer.dom(event).path
```

**After**
```js
event.composedPath()
```

---

**Before**
```js
Polymer.dom(event).rootTarget
```

**After**
```js
event.composedPath()[0]
```

---

**Before**
```js
Polymer.dom(this).observeNodes(this._nodesChanged)
```

**After**
```js
<link rel="import" href="/bower_components/polymer/lib/utils/flattened-nodes-observer.html">

this._observer = new Polymer.FlattenedNodesObserver(this._nodesChanged);
this._observer.disconnect();
```

---

**Before**  
```js
this.getComputedStyleValue()
```

**After**  
???

---

**Before**
```js
this.getContentChildren
```

**After**  
???

---

**Before**  
```js
this.getEffectiveChildren
```

**After**  
???

---

**Before**
```js
var style = this.customStyle['--my-dynamic-property'];
```

**After**  
???

---

**Before**
```js
this.customStyle['--my-dynamic-property'] = 'red';
this.updateStyles();
```

**After**
```js
this.updateStyles({'--my-dynamic-property': 'red'});
```

---

**Before**
```js
this.async(function() { /* ... */}, 100);
```

**After**
```js
setTimout(() => { /* ... */}, 100);
```

---

**Before**
```js
this.fire('some-event');
```

**After**
```js
// composed: true => bubble across the boundary between the shadow DOM and the regular DOM
this.dispatchEvent(new CustomEvent('some-event', { detail: {}, bubbles: true, composed: true }));
```
