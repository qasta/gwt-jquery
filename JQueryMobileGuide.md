

&lt;script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"&gt;



&lt;/script&gt;




Unknown end tag for &lt;/code&gt;


  1. Inherit the jQueryMobile module in your GWT Module File
> > ```xml
<inherits name='com.xedge.jquery.mobile.GWTJQueryMobile'/>```

  1. Start coding...

# Example #
  * Entry point class that changes the default PageTransition to pop and handles the Pagehide event everytime a page/div is hidden.


```java

import com.google.gwt.core.client.EntryPoint;
import com.xedge.jquery.client.JQEvent;
import com.xedge.jquery.client.JQuery;
import com.xedge.jquery.client.handlers.CommandHandler;
import com.xedge.jquery.mobile.client.JQueryMobile;
import com.xedge.jquery.mobile.client.JQueryMobile.Transition;
import com.xedge.jquery.mobile.client.handlers.PageHideEventHandler;
import com.xedge.jquery.mobile.client.model.PageHideEventValues;

public class TestGWTJQueryMobile implements EntryPoint {

public void onModuleLoad() {

JQueryMobile.init(new CommandHandler() {
@Override
public void execute() {
System.out.println("Loading jQuery Mobile");   //JQuery Mobile has been loaded

JQueryMobile.setDefaultPageTransition(Transition.pop); //change default PageTransition to pop

//add hide page handler
JQueryMobile jqueryMobileItem = JQueryMobile.getJQueryMobile(JQuery.select("div"));
jqueryMobileItem.addPagehideHandler(new PageHideEventHandler() {
@Override
public void eventComplete(JQEvent event, JQuery currentJQuery, PageHideEventValues eventValues) {
System.out.println(event.getType());     //event type
System.out.println(currentJQuery.get(0).getId());     //id of the page being hidden
System.out.println(eventValues.getNextPage().get(0).getId()); //id of the page to be loaded next
System.out.println(JQueryMobile.getOrientation());  //orientation of the device
}
});

}
});
}
}

```
**1** A JQuery object must be cast to a JQueryMobile object using JQueryMobile.getJQueryMobile().

**2** JQueryMobile can only be used once JQueryMobile.init() is called


All jQueryMobile's configuration,events,methods and utilities are available. Here is some code snippets
```java


//Configurable options
JQueryMobile.setAutoInitializePage(false);
JQueryMobile.setNS("test");
JQueryMobile.setSubPageUrlKey("testPage");
JQueryMobile.setActiveBtnClass("testclass1");
JQueryMobile.setActivePageClass("testclass2");
JQueryMobile.setAjaxEnabled(false);
JQueryMobile.setDefaultPageTransition(Transition.slideup);
JQueryMobile.setDefaultPageTransition(Transition.fade);
JQueryMobile.setDefaultPageTransition(Transition.flip);
JQueryMobile.setDefaultPageTransition(Transition.pop);
JQueryMobile.setDefaultPageTransition(Transition.slide);
JQueryMobile.setDefaultPageTransition(Transition.slidedown);
JQueryMobile.setDefaultPageTransition(Transition.none);
JQueryMobile.setDefaultDialogTransition(Transition.slidedown);
JQueryMobile.setMinScrollBack("10");
JQueryMobile.setLoadingMessage("test load");
JQueryMobile.setPageLoadErrorMessage("problems dude");
JQueryMobile.setDurationThreshold(2000);
JQueryMobile.setHashListeningEnabled(false);
JQueryMobile.setLinkBindingEnabled(false);
JQueryMobile.setOrientationChangeEnabled(false);
JQueryMobile.setPushStateEnabled(false);
JQueryMobile.setScrollSupressionThreshold(20);
JQueryMobile.setTouchOverflowEnabled(false);
JQueryMobile.setFXInterval(20);
JQueryMobile.setFXOff(true);



//Add any support conditions to be met in order to proceed
JQueryMobile.setGradeA(new ValidateHandler() {
@Override
public boolean validate() {
return true; //add custom validation rule
}
});




//Bind any event - swipeleft example
jqueryMobileItem.bind(EventType.swipeleft,new EventHandler() {
@Override
public void eventComplete(JQEvent event, JQuery currentJQuery) {
//handle event
}
});

//Handle any page event - pageload example
jqueryMobileItem.addPageloadHandler(new PageLoadEventHandler() {
@Override
public void eventComplete(JQEvent event, JQuery currentJQuery, PageLoadEventValues eventValues) {
//handle event
}
});





//Methods and utilities

JQueryMobile.changePage("test.html");   //normal changePage

ChangePageOptions changePageOptions = ChangePageOptions.create();
changePageOptions.setTransition(Transition.fade);
JQueryMobile.changePage("test.html",changePageOptions);  //changePage with custom options

JQueryMobile.loadPage("load.html") //normal loadPage

LoadPageOptions loadPageOptions = LoadPageOptions.create();
loadPageOptions.setShowLoadMsg(false);
JQueryMobile.loadPage("load.html", loadPageOptions);  //loadPage with custom options

JQueryMobile.showPageLoadingMsg();  //show loading message
JQueryMobile.hidePageLoadingMsg();  //hide loading message

JQueryMobile.showFixedToolbars();  //show fixed header/footer
JQueryMobile.hideFixedToolbars();  //hide fixed header/footer

URLSettings urlSettings = JQueryMobile.parseUrl("http://jblas:password@mycompany.com:8080/mail/inbox?msg=1234");   //parse url

JQueryMobile.makePathAbsolute("file.html", "/a/b/c/bar.html");
JQueryMobile.makeUrlAbsolute("file.html", "http://foo.com/a/b/c/test.html")
JQueryMobile.isSameDomain("http://foo.com/a/file.html", "http://foo.com/a/b/c/test.html");
JQueryMobile.isRelativeUrl("http://foo.com/a/file.html");
JQueryMobile.isAbsoluteUrl("http://foo.com/a/file.html");

JQueryMobile.silentScroll(10);  //scroll to a particular y position without triggering scroll events

JQuery activePage = JQueryMobile.getActivePage();
activePage.get(0).getId();  //id of current page in view

Integer[] resolutionBreakpoints = {100,200};
JQueryMobile.addResolutionBreakpoints(resolutionBreakpoints);  //add width breakpoints
```


Read the jQueryMobile [api docs](http://jquerymobile.com/demos/1.0/) to see all the functionality now available to you GWT apps.