---
title:  "How to add Global Links"
date:   2016-04-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `custom/Extension/application/Ext/GlobalLinks/<file>.php` and add following lines of code.

```php
<?php
$global_control_links['google'] = array(
	'linkinfo' => array(
		$app_strings['LBL_GOOGLE'] => 'http://www.google.com'
	)
);
```

Next, we will add the label, open `custom/Extension/application/Ext/Language/<language>.<file>.php`

```php
<?php
    $app_strings['LBL_GOOGLE'] = 'Google';
```
  
Navigate to Admin > Repair > Quick Repair and Rebuild. The system will then rebuild the extensions.

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
