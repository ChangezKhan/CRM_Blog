---
title:  "How to add an EntryPoint"
date:   2016-02-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `custom/Extension/application/Ext/EntryPointRegistry/customEntryPoint.php` and add following lines of code.

```php
<?php
$entry_point_registry['<ENTRY_POINT_NAME>'] = array(
    'file' => '<FILE_NAME>',
    'auth' => true
  );
```

Now, to access this file, we can use below url:

```php
<?php
'index.php?entryPoint=<ENTRY_POINT_NAME>'
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help

2016-04-01-how-to-add-global-links.markdown
