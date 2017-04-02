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
		$app_strings['LBL_SUGARCRM'] => 'http://www.sugarcrm.com'
	)
);
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
