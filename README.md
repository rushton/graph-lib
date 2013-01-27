graph-lib
=========

A simple graphing library built on top of d3

Usage
=====

```html
<html>
  <body>
    <div id="graph">
    </div>
  </body>
</html>
```
```javascript
var graph = graphLib('#graph', {width: 800, height: 600});
graph.addNodes([{id: 1, label: 'Nick Rushton'},{id:2, label: 'Rick Astley'}]);
graph.addEdges([{source: 1, target: 2}]);
```
