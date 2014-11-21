## Script

```javascript
var module  = angular.module("myapp", []).config(["$locationProvider", function($locationProvider) {
          $locationProvider.html5Mode(true); 
      }]);
 
    module.controller("mycontroller", function($scope, $http,$location) {
 
        // Authorized languages
        var languages = ['en','ja','fr']; 
        var default_lang = 'ja';
 
        // Get translations according to the 'lang' parameter
        // Default language is japanese
        var lang = $location.search()['lang'] || default_lang ;
        
        //if not in array, default value
        if(languages.indexOf(lang) < 0) lang = default_lang ;
 
        //get translation
        $http.get(lang+'.json').success (function(data){
          $scope.users = data;
      });
 
    });
```