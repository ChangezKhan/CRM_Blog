---
title:  "How to make a field mandatory only while creation a record"
date:   2017-02-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

First of all, open `view.edit.php` file of any module and in `display()` function add following lines of code.

```php
<?php
global $mod_strings;
$jsscript = <<<EOQ
<script>
    addToValidate('EditView','phone_office','varchar',true,'{$mod_strings['LBL_PHONE_OFFICE']}');    
    $('#phone_office_label').html('{$mod_strings['LBL_PHONE_OFFICE']} <font color="red">*</font>');
</script>
EOQ;
parent::display();
	
if(empty($this->bean->fetched_row['id']))
    echo $jsscript; //echo the script
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
