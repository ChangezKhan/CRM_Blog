---
title:  "How to hide 'Select' and 'Cancel' buttons from Relate field"
date:   2016-12-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `editviewdefs.php` and search for any relate field that you want to hide those buttons.

```php
<?php
'displayParams' => 
  array(
    'hideButtons' => true
  ),
```

Go to Admin and do `Quick Repair and Rebuild`.

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
