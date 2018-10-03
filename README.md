# Angular.js-Intro
In this tutorial you will create a simple angular.js application.  First create a file named "first.html" with the following content.

```
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

``` 
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
    <script src="first.js"></script>
```

Now lets set up the application in first.js

``` javascript
var firstApp = angular.module('firstApp', []);
firstApp.controller('FirstController', function($scope) {
 
});
```
Here we have created an object that is an angular.module and associated it with the string "firstApp" that we used in our html code.  We also create a controller called "FirstController".  We can use this controller in html tags in our "first.html" file.  Notice that the controller is passed an anonymous function with $scope as a variable.  The $scope object will hold variables that are shared between html and javascript.  We will often refer to the $scope as the model for our application.  So, lets add some html to use this controller in the <body> of our html file.
  
```
    <div ng-controller="FirstController">
      <span>Name:</span>
      <input type="text" ng-model="first">
      <input type="text" ng-model="last">
      <button ng-click='updateMessage()'>Message</button>
      <hr>
    </div>
```
Notice that we specify that "FirstController" should be bound to the div.  And the ng-model properties specify how data in input tags will be communicated to $scope variables.  We specify the function to be called on submit with the ng-click property.

Now lets add to the controller.  We know we will need a function "updateMessage()" which will be called when the submit button is pressed.

```javascript
  $scope.first = 'Some';
  $scope.last = 'One';
  $scope.heading = 'Message: ';
  $scope.updateMessage = function() {
    $scope.message = 'Hello ' + $scope.first +' '+ $scope.last + '!';
  };
```
All of the data and functions that are assigned to the $scope variable are available in html, so we need to define updateMessage as a $scope object function.  We also define "$scope.first" and "$scope.last".  These javascript variables will be bound to the input form ng-model elements with the same name.  So, we we are going to initialize the form to have default values.  The anonymous function passed to the controller will be run once when the page is rendered in the browser.

Now that we see how to access form data from the javascript part of our angular application, lets see how we can pass data back to the DOM elements defined in our html file.  Notice that we have created a "$scope.message" variable.  Lets try to access it from javascript.  We will do this with double "{{}}".  Add this below the "<hr>" tag.

```
{{heading + message}}
```
The body of the double "{{}}" contains variables from javascript that will be automatically updated in the DOM whenever they change in the controller.  So, when we click the submit button, the variables will automatically updated in the controller and when we change $scope variables in the controller, they will be automatically updated in the DOM.  This two way data binding is one if the coolest parts of angular.  Make sure your simple angular.js application is working.

Now lets show you some really cool magic that can occur when you have this two way data binding.  In addition to displaying the name in a message, lets put the name into a list.  First lets define a javascript array to hold an array of objects.  Then we create an object out of the form data and push it into the array.
```javascript
    $scope.names = [];
    $scope.updateMessage = function() {
        $scope.message = 'Hello ' + $scope.first + ' ' + $scope.last + '!';
        var name = {first:$scope.first,last:$scope.last};
        $scope.names.push(name);
    };
```
Now create an unordered list in our html file to display the names in the array.

```
        <ul>
            <li ng-repeat="x in names">
                {{ x.first + ', ' + x.last }}
            </li>
        </ul>
```
Notice that when an item is added to the array in the controller, it automatically updates the unordered list. 
