

&lt;script type="text/javascript" src="js/jquery-ui-1.8.21.custom.min.js" /&gt;




Unknown end tag for &lt;/code&gt;


  1. Add a link to the jQuery javascript file in your html file
> > ```xml

<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js" />
```
  1. Inherit the jQueryUI module in your GWT Module File
> > ```xml
<inherits name='com.xedge.jquery.ui.GWTJQueryUI'/>```

  1. Start coding...

# Example #
  * Entry point class that adds the jQueryUI Datepicker widget to a GWT TextBox
```java

import com.google.gwt.core.client.EntryPoint;
import com.google.gwt.user.client.ui.RootPanel;
import com.google.gwt.user.client.ui.TextBox;
import com.xedge.jquery.client.JQuery;
import com.xedge.jquery.client.handlers.CommandHandler;
import com.xedge.jquery.ui.client.JQueryUI;

public class TestGWTJQuery implements EntryPoint {
public void onModuleLoad(){
TextBox textbox = new TextBox();
textbox.getElement().setId("test");
RootPanel.get().add(textbox);
JQuery.ready(new CommandHandler() {
public void execute() {
JQuery jQueryItem = JQuery.select("#test");
JQueryUI jQueryUIItem =  JQueryUI.getJQueryUI(jQueryItem);
jQueryUIItem.datepicker();
}
});
}
}

```

**NB** A JQuery object must be cast to a JQueryUI object using JQueryUI.getJQueryUI().

You call also customize the Datepicker with the DatepickerOptions class
```java

DatepickerOptions datepickerOptions = DatepickerOptions.create();
datepickerOptions.setDuration(Duration.slow);
datepickerOptions.setShowAnim(Effect.slide);
jQueryUIItem.datepicker(datepickerOptions);

```

You can enable/disable/destroy etc. the datepicker with the DatepickerOptionParameters class.
```java

jQueryUIItem.datepicker(DatepickerOptionParameters.destroy);
jQueryUIItem.datepicker(DatepickerOptionParameters.enable);
jQueryUIItem.datepicker(DatepickerOptionParameters.disable);
```

All the remaining jQueryUI widgets and features can be implemented the same way and be customized with their corresponding Options class and their state can be changed with  their corresponding OptionParameters class.

```java

//draggable
jQueryUIItem.draggable();   //customize with DraggableOptions and change state with OptionParameters

//droppable
jQueryUIItem.droppable();   //customize with DroppableOptions and change state with OptionParameters

//resizable
jQueryUIItem.resizable();   //customize with ResizeableOptions and change state with OptionParameters

//selectable
jQueryUIItem.selectable();   //customize with SelectableOptions and change state with SelectableOptionParameters

//sortable
jQueryUIItem.sortable();   //customize with SortableOptions and change state with SortableOptionParameters

//autocomplete
AutoCompleteOptions autoCompleteOptions = AutoCompleteOptions.create();
String[] dataStringList = {"ActionScript","AppleScript","Asp","BASIC","C","C++","Clojure"};
autoCompleteOptions.setSourceStringList(dataStringList);
jQueryUIItem.autocomplete(autoCompleteOptions); //customize with AutoCompleteOptions and change state with AutoCompleteOptionParameters

//dialog
jQueryUIItem.dialog();   //customize with DialogOptions and change state with DialogOptionParameters

//progressbar
jQueryUIItem.progressbar();   //customize with ProgressbarOptions and change state with ProgressbarOptionParameters

//slider
jQueryUIItem.slider();   //customize with SliderOptions and change state with SliderOptionParameters

//tabs
jQueryUIItem.tabs();   //customize with TabsOptions and change state with TabsOptionParameters

```

All the jQueryUI effects,animations and utilities are also available.

Read the jQueryUI [docs](http://jqueryui.com/demos/) to see all the functionality and widgets now available to you GWT apps.