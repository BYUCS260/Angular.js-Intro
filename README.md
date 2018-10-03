# Angular.js-Intro
In this tutorial you will create a simple angular.js application.  First create a file named "first.html" with the following content.

``` javascript
<!doctype html>
<html ng-app="firstApp">
  <head>
    <title>First AngularJS App</title>
  </head>
  <body>
  </body
</html>
```
The html looks fairly familiar except that the html tag includes a ng-app property.  This property defines which application will be used for this DOM element.  Angular will implement two way data binding, so that any variable that changes in the javascript scope for "firstApp" will be reflected in this html element.  Now import the angular javascript library and the javascript code "first.js".  you can put it right before the closing body tag.

``` javascript
    <script src="http://code.angularjs.org/1.2.9/angular.min.js"></script>
    <script src="first.js"></script>
```

Now lets set up the application in first.js

``` javascript
var firstApp = angular.module('firstApp', []);
firstApp.controller('FirstController', function($scope) {
 
});
```
Here we have created an object that is an angular.module and associated it with the string "firstApp" that we used in our html code.  We also create a controller called "FirstController".  We can use this controller in html tags in our "first.html" file.  Notice that the controller is passed an anonymous function with $scope as a variable.  The $scope object will hold variables that are shared between html and javascript.  So, lets add some html to use this controller in the <body> of our html file.
  
```javascript

```
