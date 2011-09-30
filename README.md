jsMessage
=========

Custom notifications, alerts, confirmations

This library was extracted from code of [DHTMLX suite][dhtmlx].

Library can be used under terms of [MIT license][mit] (basically **free**) .

Only **3kb** gzipped, without external dependencies.

Works in FF, Chrome, Safari (including iPhone), Opera, IE7+

Supported message types
-----------------------

jsMessage offers 7 message window variations at your disposal (3 main types and a few subtypes):

- alert
  - alert (default)
  - alert-warning
  - alert-error
- confirm
 - confirm (default)
 - confirm-warning
 - confirm-error
- notice


How to use
-----------

The type (subtype) of the message window is specified through the parameter type. The default value is notice.

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
	                type: "alert-warning",
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

### Notice

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

Default delay of notices can be set as

```javascript
	dhtmlx.message.expire = 4000; //time in milliseconds
	t.position = "top";	
```

Default position of notices can be set as

```javascript
	dhtmlx.message.position = "top";	 // possible values "top" or "bottom"
```

[dhtmlx]: http://dhtmlx.com/docs/products/dhtmlxSuite/index.shtml?message
[mit]: http://en.wikipedia.org/wiki/MIT_License