# Example #
  * Entry point class that uses jQuery to set the border of a div to "3px solid red" and then changes it to blue on click.
```java

import com.google.gwt.core.client.EntryPoint;
import com.google.gwt.user.client.ui.HTML;
import com.google.gwt.user.client.ui.RootLayoutPanel;
import com.xedge.jquery.client.JQEvent;
import com.xedge.jquery.client.JQuery;
import com.xedge.jquery.client.handlers.CommandHandler;
import com.xedge.jquery.client.handlers.EventHandler;

public class TestGWTJQuery implements EntryPoint {
public void onModuleLoad() {
RootLayoutPanel.get().add(new HTML("<div id=\"test1\">hello world</div"));
JQuery.ready(new CommandHandler() {
@Override
public void execute() {
JQuery.select("#test1").css("border", "3px solid red");
JQuery.select("#test1").click(new EventHandler() {
@Override
public void eventComplete(JQEvent event, JQuery currentJQuery) {
currentJQuery.css("border", "3px solid blue");
}
});
}
});
}
}
```

**1** You can only start using JQuery once JQuery.ready() is called.
**2** JQuery.select() is used instead of $() since "$" has special meaning in GWT.

Read the jQuery [docs](http://docs.jquery.com/Main_Page) to see all the functionality now available to you GWT apps.