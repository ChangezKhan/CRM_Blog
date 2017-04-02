---
title:  "How to remove Global Links"
date:   2016-03-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `custom/Extension/application/Ext/GlobalLinks/<file>.php` and add following lines of code.

```php
<?php
if (isset($global_control_links['<NAME_OF_LINK>']))
{
	unset($global_control_links['<NAME_OF_LINK>']);
}
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
