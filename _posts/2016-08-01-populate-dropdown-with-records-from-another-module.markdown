---
title:  "How to populate dropdown with records from another module"
date:   2016-08-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

Consider, we have two modules `A` & `B`. And we want to show all records of module `A`, to show in module `B` as a dropdown.

First of all, we will create a logic hook in module `A` to get all records and store it into any dropdown. So, let's create new dropdown using `Dropdown Editor`, so we can use it in our logic hook file.

This is following code you should add to logic hook file:

```php
<?php
	if(!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');
		
	require_once('modules/ModuleBuilder/MB/ModuleBuilder.php');
	require_once('modules/ModuleBuilder/parsers/parser.dropdown.php');
	
	/**
	* Motive : To update the Dropdown editor with the new record as Dropdown using After save logic hook
	*/

	class StudioUpdate 
	{
		function save_dd($dd_name,$new_dd_arr)
		{
			$parser = new ParserDropDown();
			$params = array();
			$_REQUEST['view_package'] = 'studio';
			$params['view_package'] = 'studio';
			$params['dropdown_name'] = $dd_name;
			$params['dropdown_lang'] = 'en_us';
			$json = getJSONobj();
			$params['list_value'] = $json->encode($new_dd_arr);
			$parser->saveDropDown($params);
		}

		function StudioUpdate($bean,$arg,$events) 
		{
			global $db;

			$related_queue_arr = array();
			$related_queue_arr[''] = '';
			
			$dropdown_list_name = '<DropDown_List_Name>'; // Newly created DropDown List name
			$properties['options'] = $dropdown_list_name;

			$selectQueue_list = "SELECT id,name FROM <MODULE_NAME> WHERE deleted=0";
			$selectQueue_list_res = $db->query($selectQueue_list);
			$new_dd_arr[] = array('','');
			
			while($selectQueue_list_res_row = $db->fetchByAssoc($selectQueue_list_res))
			{
				$related_queue_arr[$selectQueue_list_res_row['id']] = $selectQueue_list_res_row['name'];
				$new_dd_arr[]=array($selectQueue_list_res_row['id'],$selectQueue_list_res_row['name']);
			}
						
			$GLOBALS['app_list_strings'][$dropdown_list_name] = $related_queue_arr;
			$this->save_dd($properties['options'],$new_dd_arr);
		
		}
	}
```

And that's it. Create records and check if that record is reflected in dropdown or not.

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
