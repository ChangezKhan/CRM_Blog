---
title:  "How to get dropdown options in JavaScript"
date:   2016-06-01 15:04:23
categories: [SugarCRM]
tags: [SugarCRM]
---

We can use the following code to fetch dropdown options.

```php
<?php
var statusOptions = SUGAR.language.languages.app_list_strings['case_status_dom'];
```

You can loop through them to create an dropdown in JS itself.

```php
<?php
var status_dd = "<select name= 'status' id='status'>";

for(var key in statusOptions){ 
    // Here "key" gives the key of options and "statusOptions[key]" gives the value of it. 
    status_dd += '<option value="'+key+'">'+statusOptions[key]+'</option>';    
}
status_dd +="</select>";
```

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
