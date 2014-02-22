jqAlert
=======
With the use of jQuery and jQuery UI there do you really want to use the basic javascript dialog alerts? Personally there is absolutely no way I am going to use the dinosaur based JavaScript alerts.

### History
What drove me to create jqAlert?

With the use of jQuery and jQuery UI, I had all of the performance and visual improvements that I ever dreamed of in javascript. So when it came down to dialog based alerts, I just knew there was absolutely no way that I was going to use those dinosaur based JavaScript alerts. I had seen several different options out there and it seemed like everyone had their own flavor.

There is already such a great group of developers and I probably could have searched to the ends of the earth however I felt my needs were specific. So I created the initial version which did nothing but a basic alert message and implemented some other features that I needed.

I continued to work on it and with each revision I added new features till I came to a point where I thought I should share what I had created with others. So that is when I wrote the article [jQuery UI Alerts Dialog using ThemeRollers](http://www.codeproject.com/Articles/295236/jQuery-UI-Alerts-Dialog-using-ThemeRollers) describing my idea and approach.

### Action
I will go over some basic examples here but you can get more information and better examples with actual demonstrations at the following location:

[jqAlert.com](http://jqalert.com/)

### Usage

#### Alert Dialogs
A basic example of how to display an alert.

```javascript
$.alert('Here is a very basic alert message.', {
    title:"Basic Alert" 
});
```

In the event that you want to know when things are happening (dialog closed, button clicked) you can include callbacks.

```javascript
$.alert('jqAlert is easy to use with alerts and its where I got my start.', {
    title:'Alert Title Message',
    onClose: function() { 
    	console.log('dialog has been closed.');
    },
    buttons:[
        {
            title:'Press Me',
            callback:function() { 
            	console.log('user pressed the OK button.')
            	$(this).dialog("close");
            }
        }
    ]
});
```

#### Confirmation Dialogs
A basic example of how to display a confirmation.

```javascript
$.confirm('So from this dialog do you notice the confirmation buttons?', {
    title:'Confirmation Prompt'
})
```

This is most likely where you will want to use callbacks.

```javascript
$.confirm('jqAlert is easy to use when you want to get a confirmation.',{
    title:'Confirm Message Title',
    onClose: function() { 
    	console.log('dialog has been closed.');
	},
    buttons:[
        {
            title:'Yes',
            callback:function() { 
            	console.log('user pressed Yes button');
            	$(this).dialog("close");
            }
        },
        {
            title:'No',
            callback:function() { 
            	console.log('user pressed No button');
            	$(this).dialog("close");
        	}
        },
        {
        	title:'Cancel',
        	callback:function() {
        		console.log('user pressed Cancel button');
            	$(this).dialog("close");
        	}
		}
    ]
});```

#### Prompt Dialogs
A basic example of how to display a prompt.

```javascript
$.prompt('So from this dialog you can prompt the user for information.', {
    title:"Basic Prompt", 
    defaultResult:"Default user message"
});
```
This again is most likely where you will want to use callbacks.

```javascript
$.prompt('jqAlert is easy to use with prompt dialogs that get information from the user.', {
    title:'Prompt Message Title',
    defaultResult:'Some default response',
    onClose: function() { 
    	console.log('dialog has been closed.');
	},
    buttons:[
        {
            title:'Ok',
            callback:function() { 
                $.alert($(this).find('#result').val());
                $(this).dialog("close");
            }
        },
        {
            title:'Cancel',
            callback:function() { 
            	console.log('user pressed the cancel button');
            	$(this).dialog("close");
            }
        },
        {
            title:'Help',
            callback:function() { 
            	console.log('user pressed the help button');
            	$(this).dialog("close");
            }
        }
    ]
});
```

#### Inform Dialogs
The inform dialog supports all of the default properties and callback notifications. The only exception that the inform dialog has over the dialogs is that it does not support buttons.

```javascript
// an inform dialog with an 8 second timeout 
$.inform('jqAlert is easy to use when you want an timed info message.', {
    title:'Inform Title', 
    timer:8000,
    icon:'',
    customIcon:'icon-asterisk',
    allowEscape:false,
    onTimeout: function() { $.alert('timed out');}
});
```
