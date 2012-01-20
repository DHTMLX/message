jsMessage
=========

Custom notifications, alerts, confirmations

This library was extracted from code of [DHTMLX suite][dhtmlx].

- Library can be used under terms of [MIT license][mit] (basically **free**).
- Only **4kb** gzipped, without external dependencies.
- Works in FF, Chrome, Safari (including iPhone), Opera, IE7+

Live samples can be checked at [http://dhtmlx.github.com/message/][message]

Supported message types
-----------------------

jsMessage offers 4 variations at your disposal:

- alert
- confirm
- notification ( message )
- modalbox

How to use
-----------

The type (subtype) of the message window is specified through the parameter type. The default value is "message".

```javascript
	dhtmlx.message({ 
	    type:"confirm-warning", 
	    text:"Are you sure you want to do it?"
	})
```

or, you can use separate methods

```javascript
	dhtmlx.confirm({
	    title:"Confirm",
	    text:"Continue?"
	});
	//or
	dhtmlx.alert({
	    title:"Alert",
	    type:"alert-error",
	    text:"You can do this"
	});
	//or
	dhtmlx.modalbox({
	    title:"Settings",
	    text:"Abstract popup"
	});	
```

Styling
-------
For any type of the message window you can define a custom style to achieve the desired look. 
Generally, the appropriate css class is specified through the parameter type: you define a css class and set the parameter to its name.

```html
	<style type="text/css">
		.dhtmlx-myCss{
			font-weight:bold !important;
			color:white !important;
			background-color:red !important;
		}
	</style>
	<script>
		dhtmlx.message({ type:"myCss", text:"some text" });
	</script>
```

Options
---------

### Alert

- title - (string) the text of the header (by default, 'Alert').
- type - the subtype of the window or a custom css class. The default value for the window - 'alert'.
- text - (string) the text of the window body.
- ok - (string) the text of the 'Ok' button.
- callback - (function) the function called on button click
- position - for now support only one value "top", any other value will result in center align
- width - width of the modal box ( samples "100px", "50%")
- height - height of the modal box 

**Full form**

```javascript
	dhtmlx.message({
			title: "Close",
	                type: "alert",
			text: "You can't close this window!",
			callback: function() {dhtmlx.alert("Test alert");}
	})
//or
	dhtmlx.alert({
			text: "Download is completed.",
			callback: function() {dhtmlx.alert("Test alert");}
	})
```

**Short form**

```javascript
	dhtmlx.alert("someText");
```

Both alert and confirm blocks keyboard input while active. Pressing SPACE or ENTER will close message with positive result. Pressing ESC will close message with negative result. (you can use dhtmlx.message.keyboard = false; to disable this behavior)

### Confirm

- title - (string) the text of the header (by default, 'Alert').
- type - the subtype of the window or a custom css class
- text - (string) the text of the window body.
- ok - (string) the text of the 'Ok' button.
- cancel - (string) the text of the 'Cancel' button.
- callback - (function) the function called on button click. Receives 'true' or 'false' as the parameter (subject to the clicked button).
- position - for now support only one value "top", any other value will result in center align
- width - width of the modal box ( samples "100px", "50%")
- height - height of the modal box 

**Full form**

```javascript
	dhtmlx.message({
		type:"confirm",
		text: "Continue?",
		callback: function() {dhtmlx.confirm("Test confirm");}
	});
//or
	dhtmlx.confirm({
		title: "Close",
	            type:"confirm-warning",
		text: "Are you sure you want to do it?",
		callback: function() {dhtmlx.confirm("Test confirm");}
	});
```

**Short form**

```javascript
	dhtmlx.confirm("ConfirmText");
```

### ModalBox

- title - (string) the text of the header (by default, 'Alert').
- type - the subtype of the window or a custom css class
- text - (string) the text of the window body.
- ok - (string) the text of the 'Ok' button.
- cancel - (string) the text of the 'Cancel' button.
- callback - (function) the function called on button click. Receives 'true' or 'false' as the parameter (subject to the clicked button).
- buttons - array of labels, each one will be converted to the button ( much like multi-button confirm ). Callback function will receive index of pressed button ( 0 - for first button, 1 - for second button and etc. )
- position - for now support only one value "top", any other value will result in center align
- width - width of the modal box ( samples "100px", "50%")
- height - height of the modal box 
- content - can be used instead of text, defines html element (or its ID) which will be shown inside of a popup

**Examples**

```javascript
	dhtmlx.modalbox({
		title:"Settings"
		text: " ... html code here... ",
		buttons:["Save", "Defaults", "Cancel"],
		callback:process_result
	});
```

function returns the html container of the box which can be used for some actions

```javascript
	var box = dhtmlx.modalbox(...);
	box.getElementsByTagName("input")[0].focus();
	...
	dhtmlx.modalbox.hide(box); //hide popup  
```

####  Closing modal box

There are 3 way to close modal box 

- call dhtmlx.modalbox.hide(box) - where "box" is result of dhtmlx.modalbox command
- call dhtmlx.modalbox.hide(node) - where node - any html node in the box (allows to create "close" links easily)
- click on any button, which was defined through "buttons" property
       
```javascript
	var box = dhtmlx.modalbox({
		text:"<a href='#' onclick='dhtmlx.modalbox.hide(this)'>Click to close<a>"
	});
```


#### Custom buttons

You can place a custom button in the popup, which is styled exactly as default message buttons. To do so you need to place the next html snippet

```javascript
	var box = dhtmlx.modalbox({
		text:"<span class='dhtmlx_button'><input type='button' value='Press me'></span>"
	});
```

#### Content reusage

Instead of setting html text you can place any html container on the page in the modalbox

```html
	<div id='mycontent'>Some form here </div>
```

```javascript
	var box = dhtmlx.modalbox(content:"mycontent");
```

after box will be closed, you can reopen it by 

```javascript
	dhtmlx.modalbox(box);
```


### Notification (message)

- type - the subtype of the window or a custom css class. The default value for the window - 'alert'.
- text - (string) the text of the window body.
- expire - the time after passing which the window disappears (in milliseconds). You can use negative value (-1) to make notice persistent. 

**Full form**

```javascript
	dhtmlx.message({
		text:"An error has occured.<br /> Please, see the log file!",
		expire:1000, You can use negative value (-1) to make notice persistent. 
		type:"customCss" // 'customCss' - css class
	});
```

**Short form**

```javascript
	dhtmlx.message("Your data has been successfully saved!");
```

Extra configuration
-------------------

Default delay of notifications can be set as

```javascript
	dhtmlx.message.expire = 4000; //time in milliseconds
	t.position = "top";	
```

Default position of notices can be set as

```javascript
	dhtmlx.message.position = "top";	 // possible values "top" or "bottom"
```


Interaction with alert and confirm from keyboard can be disabled by 

```javascript
	dhtmlx.message.keyboard = false;	 // possible values "top" or "bottom"
```

### Alert subtypes

For all kinds of messages, there are alert variations, which can be used for more important notifications

```javascript
	dhtmlx.message({ type:"error", "Critical error!"});
	//or
	dhtmlx.message({ type:"alert-error", "Critical error!"});
	//or
	dhtmlx.message({ type:"confirm-error", "Confirm self-destruction!"});
```

[dhtmlx]: http://dhtmlx.com/docs/products/dhtmlxSuite/index.shtml?message
[message]: http://dhtmlx.github.com/message/
[mit]: http://en.wikipedia.org/wiki/MIT_License