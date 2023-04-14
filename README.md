![GitHub issues](https://img.shields.io/github/issues/leandrosardi/listsjs) ![GitHub](https://img.shields.io/github/license/leandrosardi/listsjs) ![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/leandrosardi/listsjs) ![GitHub last commit](https://img.shields.io/github/last-commit/leandrosardi/listsjs)


**UNDER CONSTRUCTION - CHECK BACK IN A FEW DAYS**

# Lists.Js
The **Lists.Js** is a little HTML widget to manage favourite lists on your UI.

**>>>> IF YOU LIKE THIS PROJECT, STAR IT ! <<<<** 

**Features**

- Setup button text.
- Setup button color.
- Array of lists.
- Disabled (deleted) items.
- Event handler for before checking a list.
- Event handler for before unchecking a list.
- Event handler for before creating a list.
- Event handler for when the list is expanded, to fill it by ajax in order to reduce the page-load-time.
- Function to get list details by its id.
- Function to draw the component.


## 1. Getting Started
Get started in 3 simple steps.

1. Download the required libraries and stylesheets.
All these files are included in this project. You can download them from this page.

2. Include them in the <header> section of your HTML page.

```html
<script src="jquery-3.5.1.min.js" type="text/javascript"></script>
<script src="commons.js" type="text/javascript"></script>
<link rel="stylesheet" href="./templates.css">
<script src="./lists.min.js" type="text/javascript"></script>
```

3. Create a nice list of favorites.

```html
<div id='playlists' style='width:750px;'> </div>
<script>
	$(document).ready(function() {
		// simple filter
		var playlists = document.getElementById('playlists');	  

		listsJs.draw(playlists, {
			id: '123',
			caption: 'Playlists',
			color: 'blue',
			lists: [{
				id: '1',
				name: 'list1',
				checked: true,
				deleted: false
			}, { 
				id: '2',
				name: 'list2',
				checked: false,
				deleted: false
			}, { 
				id: '3',
				name: 'list3',
				checked: false,
				deleted: true
			}],
			on_check_item: function(h) {
				// call ajax before the list is marked as checked
				// return true if ajax worked fine, and list check is allowed.
				return true;
			},
			on_uncheck_item: function(h) {
				// call ajax before the list is marked as unchecked
				// return true if ajax worked fine, and list uncheck is allowed.
				return true;
			},
			on_add_item: function(h) {
				// call ajax before the new list is added
				// return a value for the ID of the new element.
				// return nul if new element is not allowed to be added because of ajax error.
				return true;
			},
			on_expand: function() {
				// disable add button and text input while loading
				listsJs.disable_add_button(playlists);
				listsJs.disable_add_input(playlists);
				// use this list to call ajax to get all items, in order to reduce the loadtime of the page when you are managing many compenents
				listsJs.set_loading(playlists, true);

				// re-enable add button and text input when ajax finishes
				//listsJs.enable_add_button(playlists);
				//listsJs.enable_add_input(playlists);
			}
		});
	});
</script>
```

## 4. Real-Life Example

_(it is pending to add the links to the examples)_

- Streaming Playlists
- CRM Leads Tagging

## 5. Using Lists.Js as a [MySaaS](https://github.com/leandrosardi/mysaas) Extension

If you are running a [MySaaS](https://github.com/leandrosardi/mysaas) project, you can add **Lists.Js** as an extension.

Such an extension includes a code example screen (`/listsjs`) that you show to other developers, for reference. 

Install **Lists.Js** as an extension of [MySaaS](https://github.com/leandrosardi/mysaas) is pretty simple.

**Step 1:** Clone the project in the `extensions` filder.

```bash
cd ~/code/mysaas/extensions
git clone https://github.com/leandrosardi/listsjs
```

**Step 2:** Add the extension to your `config.rb` file.

```ruby
BlackStack::Extensions.append :listsjs
```

## 6. Additional Notes

The **Lists.Js** library is just starting on Apr-2023, and more functions will be added as needed.

The **Lists.Js** library has been written following the [**W3C JavaScript Best Practices**](https://www.w3.org/community/webed/wiki/JavaScript_best_practices).

## 7. Disclaimer

Use at your own risk. The use of the software and scripts downloaded on this site is done at your own discretion and risk and with agreement that you will be solely responsible for any damage to any computer system or loss of data that results from such activities.

## 8. Maintainer

Leandro Daniel Sardi <leandro((dot))sardi((@))connectionsphere.com>