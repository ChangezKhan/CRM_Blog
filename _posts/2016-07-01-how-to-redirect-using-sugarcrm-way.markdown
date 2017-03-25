---
title:  "How to redirect to any page using SugarCRM way"
date:   2016-07-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

We can use the following code to redirect to any page using SugarCRM way.

```php
<?php
$params = array(
	'module'=> '<MODULE_NAME>',
	'action'=>'<VIEW_NAME>',
);

SugarApplication::redirect("index.php?" .http_build_query($params));
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
