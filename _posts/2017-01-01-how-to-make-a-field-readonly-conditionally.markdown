---
title:  "How to make a field 'ReadOnly' conditionally"
date:   2017-01-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `view.edit.php` file of any module and in `display()` function add following lines of code.

```php
<?php
global $current_user;
// check if current user is in specific role
	
$IS_AM = in_array("<ROLE NAME>", ACLRole::getUserRoleNames($current_user->id));
if($IS_AM)
	$this->ev->ss->assign('readOnly', 'readonly = "readonly"');
else
	$this->ev->ss->assign('readOnly', '');
```

Now, open `editviewdefs.php` file of same module and give following custom code to any desired field.

```php
<?php
'customCode' => '<input type="text" class="phone" tabindex="0" title="" value="{$fields.<FIELD_NAME>.value}" maxlength="100" size="30" id="<FIELD_ID>" name="<FIELD_NAME>" {$readOnly}>',
```

Go to Admin and do `Quick Repair and Rebuild`.

If you wish to make this field `ReadOnly` only while editing the record, add following condition 

```php
<?php
if($IS_AM && !empty($this->bean->id))
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
