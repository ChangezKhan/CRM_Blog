---
title:  "How to remove sorting links from ListView/Subpanel"
date:   2016-05-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `custom/modules/<ANY_MODULE>/metadata/listviewdefs.php` or `custom/modules/<ANY_MODULE>/metadata/subpaneldefs.php` file and search for the array of any field and add following code.

```php
<?php
sortable => false
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
