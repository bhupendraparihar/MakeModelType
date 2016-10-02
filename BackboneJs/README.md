The starting point to code in Backbone is to think about data. As the saying says. 

> Getting Truth Out of the DOM

Start with Car Constructor
```javascript
var Car = function(make, model, type) {
  this.make = make;
  this.model = model;
  this.type = type;
}
```
Creating Backbone Model equivalent to above code
```javascript
var Car = Backbone.Model.extend({
  defaults: {
    make:'',
    model:'',
    type:'new'
  }
});
```
type is by default 'new' and type can only be 'used' or 'new'

```javascript
var Car = Backbone.Model.extend({
  defaults: {
    make:'BMW',
    model:'X6',
    type:'new'
  },
  
  validate: function(attrs) {
    if( attrs.type !== 'new' || attrs.type !== 'used') {
      return 'Type can only be new or used'
    }
    
    if( ! attrs.make ) {
      return 'Every car should have a make';
    }
    
    if( ! attrs.mode ) {
      return 'Every car should hava a model';
    }
  }
});

var car = new Car('BMW','X6','new');
car.set('type','something else');

car.on("error", function(model, error) {
  console.log(error);
});
```
