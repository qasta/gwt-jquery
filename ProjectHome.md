A GWT library that wraps the existing **jQuery** , **jQuery UI**  and **jQuery Mobile** javascript libraries.

Now GWT developers can use these popular libraries in their GWT applications in Java.

This library completely wraps the latest jQuery libaries so you can look at the corresponding Javascript documentation for [jQuery](http://docs.jquery.com/Main_Page),[jQuery UI](http://jqueryui.com/demos/) and [jQuery Mobile](http://jquerymobile.com/demos).

The major difference is that the $() selector in Javascript is replaced with JQuery.select() in Java.

**Example1** - set css border property
```java

//javascript
$("#test").css("border","3px solid red");
```
is replaced with
```java

//java
JQuery.select("#test").css("border","3px solid red");
```

**Example2** - add click handler
```java

//javascript
$("#test").click(function(event) {
//event handling code goes here
});
```
is replaced with
```java

//java
JQuery.select("#test").click(new EventHandler() {
public void eventComplete(JQEvent event, JQuery currentJQuery) {
//event handling code goes here
}
});
```

Read the [User Guides](http://code.google.com/p/gwt-jquery/w/list) and start coding.

[follow me on twitter](http://twitter.com/#!/alessioh) or mail me on gmail if you have any questions.

**NB** This is a JSNI wrapper of the existing Javascript libraries it is NOT a port. A port of jQuery to GWT can be found at http://code.google.com/p/gwtquery/ . I decided to wrap the existing libraries because it will be relatively easy to stay up to date with the latest Javascript  versions instead of reimplementing it in java.