# jbind
A small JavaScript UI binding framework. Supports select and table elements and hides the details of the DOM tree. It also support most other simple UI elements like input, checkbox, textarea, img.  
Published under MIT License  
  
[![License: MIT](https://img.shields.io/github/license/mku11/jbind.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-blue)](https://github.com/mku11/jbind/releases)
[![GitHub Releases](https://img.shields.io/github/downloads/mku11/jbind/latest/total?logo=github)](https://github.com/mku11/jbind/releases)

# Supported DOM Elements:
Although these tags are supported not all fields are supported.  
* select
* table
* textarea
* span
* input (text, checkbox)
* progress
* img
* video (minimal support)
* iframe (minimal support)

## Examples
1. Bind an observable list to a table
HTML:
```
<table id="table" class="table">
	<thead class="table-header">
	</thead>
</table>
```

JS:
```
    let list = JBind.bind(document, 'table', 'tbody', new ObservableList());
	
	// add an item
	let item = new MyItem();
	list.add(item);
	list.insert(2, item); // insert at specific position
	
	// select this item
	// class tr-row-selected is added to the table row (use css to colorize, etc)
	list.select(item); 
	
	// add a double click listener
	list.onItemDoubleClicked = (index) => {
		let itemClicked = list.getItem(index);
	};
	
	// notified when item is selected
	list.addSelectedChangeListener(() => {
		let selectedItem = list.getSelectedItems();
	});
		
	// scroll to item at index
	list.bringIntoView(2);
	
	// remove item
	list.remove(item);
	
	// remove item at position
	list.removeAt(2);
	
	// clear all items
	list.clear();
```

2. Bind an observable list to a select options property  
HTML:
```
<select id="car-type">
</select>
```

JS:
```
    let list = JBind.bind(this.contentWindow.getRoot(), 'car-type', 'options', new ObservableList());
	
	// add an item
	let item = "Car1";
	list.add(item);
	item = "Car2";
	list.add(item);
	list.insert(2, item); // insert at specific position
	
	// select this item
	list.select(item); 
	
	// notified when item is selected
	list.addSelectedChangeListener(() => {
		// get the selected item
		let selectedItem = list.getSelectedItems();
	});
	
	// remove item
	list.remove(item);
	
	// remove item at position
	list.removeAt(2);
	
	// clear all items
	list.clear();
```