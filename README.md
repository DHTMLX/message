jsMessage
=========

Custom notifications, alerts, confirmations

This library was extracted from code of [DHTMLX suite][dhtmlx].

- Library can be used under terms of [MIT license][mit] (basically **free**).
- Only **3kb** gzipped, without external dependencies.
- Works in FF, Chrome, Safari (including iPhone), Opera, IE7+

Live samples can be checked at [http://dhtmlx.github.com/message/][message]

Supported message types
-----------------------

jsMessage offers 3 variations at your disposal:

- alert
- confirm
- notification ( message )


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
	    text:"You can't do this"
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
- type - the subtype of the window or a custom css class. The default value for the window - 'alert'.
- text - (string) the text of the window body.
- ok - (string) the text of the 'Ok' button.
- cancel - (string) the text of the 'Cancel' button.
- callback - (function) the function called on button click. Receives 'true' or 'false' as the parameter (subject to the clicked button).

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