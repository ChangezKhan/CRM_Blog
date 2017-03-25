---
title:  "How to add a custom href link on any field"
date:   2016-01-08 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First we will add following code to a field, on which we want hyper link on it to following file:

`custom\modules\<MODULE_NAME>\metadata\<ANY_VIEW>viewdefs.php`

Now find the add the following code to an array of field, on which you want to see hyper link.

```php
'customCode' => '{$CSTM_URL}'
```

Now, add following code to `view.<ANY_VIEW>.php`

```php
<?php
$link = "<YOUR_LINK>";
$field = $this->bean-><VALUE_OF_FIELD>;
$custom_url = "<a href='" .$link ."' >" .$field ."</a>";
$this->ss->assign("CSTM_URL", $custom_url);
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
