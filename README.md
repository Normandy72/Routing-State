# Routing State with resolve
### Step 1: Set up resolve Property
```
.state('view1', {
    url: '/view1',
    templateUrl: 'view1.html',
    controller: 'ViewCtrl as view1',
    resolve: {
        myData: ['Service', function(Service){
            return Service.getData();
        }]
    }
});
```
` myData` - return value is injected into View1Ctrl as 'myData'
### Step 2: Inject Resolve Property Into Controller
```
View1Ctrl.$inject = ['myData'];
function View1Ctrl(myData){
    var view1 = this;
    view1.myData = myData;
}
```

#### Resolve Properties Can Be Anything
```
.state('view1', {
    url: '/view1',
    templateUrl: 'view1.html',
    controller: 'View1Ctrl as view1',
    resolve: {
        myData: 'some data'
    }
});
```