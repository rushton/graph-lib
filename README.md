graph-lib
=========

A simple graphing library built on top of d3

Usage
=====

Set up our html:
```html
<html>
   <head>
      <script src="d3.min.js"></script>
      <script src="graphlib.js"></script>
      <style type="text/css">
         .node circle{
            fill: #eee;
            stroke: #f0f;
         }   
         .link {
            stroke: #666;
         }   

      </style>
   </head>
   <body>
      <div id="graph">
      </div>
   </body>
</html>
```    

The graphing javascript:
```javascript
var graph = graphLib('#graph', {width: 800, height: 600});
graph.addNodes([{id: 1, label: 'Nick Rushton'},{id:2, label: 'Rick Astley'}]);
graph.addEdges([{source: 1, target: 2}]);
```
