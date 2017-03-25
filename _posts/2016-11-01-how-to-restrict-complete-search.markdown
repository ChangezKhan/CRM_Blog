---
title:  "How to restrict complete search"
date:   2016-11-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First copy `view.list.php` file from following location to a custom directory of a any module

`include\MVC\View\views\view.list.php`

Now in `view.list.php` file, in `listViewProcess` function, add following lines of code

```php
<?php
global $current_user;

$check_search = array_filter($this->lv->searchColumns);

if (empty($check_search)) 
{
	echo "<b><font color='red'>Complete Search Restricted</font></b>";
	return;	
}
```
That's it.

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
