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

Hiding nodes:
```javascript
var graph = graphLib('#graph', {width:800, height: 600});
graph.addNodes([{id:1, label:'Above & Beyond', type:'trance'},
                {id:2, label:'Jaytech', type:'trance'},
                {id:3, label:'John B', type: 'Drum & Bass'},
                {id:4, label:'Netsky', type:'Drum & Bass'},
                {id:5, label:'Danny Byrd', type: 'Drum & Bass'}]);
                
graph.addEdges([{source: 1, target: 2},
                {source: 1, target: 3}, 
                {source: 2, target: 3},
                {source: 3, target: 4},
                {source: 3, target: 5},
                {source: 4, target: 5}]);

// hide all trance nodes & connected edges
graph.hide({type: 'trance'});

//show the trance edges after 5 seconds
setTimeout(function(){ 
   graph.show({type:'trance'});
 
   // keep the node with id 1 hidden, then show it again after 2 seconds
   graph.hide({id:1});
   setTimeout(function(){
       graph.show({id:1});
   }, 2000);
}, 5000);
```


Node Specification
==================
```js
{
   label: <string|string[]: label for the node, given an array uses line-breaks>,
   id:    <unique-id: a unique id for the node>,
   type:  <string: a type to be used for styling>
}
```

Edge Specification
==================
```javascript
{
   source: <id: id of source node to connect to>,
   target: <id: id of the target node to connect to>,
   label:  <string: label which will attach to the line in the center>
}
```

Config
======
```javascript
{
      /**
       * width of the canvas
       */
      width: 960,
      /**
       * height of the canvas
       */
      height: 800,
      /**
       * whether or not the graph should be zoomable
       */
      zoomable: true,
      /**
       * a function to call when a node is clicked
       */
      click: function(){},
      /**
       * a function to call when a node is moused over
       */
      mouseover: function(){},
      /**
       * a function to call when a node is moused out
       */
      mouseout: function(){},
      /**
       * charge of the nodes, can also be a function
       */
      charge: -150,
      /**
       * node's gravity
       */
      gravity: 0.1,
      /**
       * strength between the links
       */
      linkStrength: 0.1,
      /**
       * constant which scales the link lengths
       */
      linkLengthConstant: 5,
      /**
       * link style can be one of the following:
       *  'straight' - straight line from node to node
       *  'bezier' - slightly curved lines from node to node
       *  'arc' - arced line to the node
       */
      linkStyle: 'straight',
      /**
       * function which runs every tick of the graph
       */
      tick: tock,

      /**
       * contains types and styles for elements
       * each entry has a key of the type to apply the style to
       * the value contains an object which has:
       *    type - the type of element to use for this type of node
       *    attributes - attributes to apply to the node
       */
      style: {
         defaultStyle: { tag: 'circle', attributes: {r: 5} }
      }
   }
```
