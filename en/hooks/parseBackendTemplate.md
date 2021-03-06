parseBackendTemplate
--------------------

The `parseBackendTemplate` hook is triggered when a back end template is parsed. It passes the template content and the template name as arguments and expects the template content as return value. It is available from version 2.6.0.


### Parameters ###

1. *string* `$strContent`

	Content of the parsed backend template.

2. *string* `$strTemplate`

	The template name (e.g. `be_widget`) without file extension.


### Example ###

```php
<?php

// config.php
$GLOBALS['TL_HOOKS']['parseBackendTemplate'][] = array('MyClass', 'myParseBackendTemplate');

// MyClass.php
public function myParseBackendTemplate($strContent, $strTemplate)
{
    if ($strTemplate == 'be_main')
    {
        // Modify output
    }

    return $strContent;
}
```


### See Also ###

- [parseFrontendTemplate](parseFrontendTemplate.md) - triggered when a front end template is parsed
- [outputFrontendTemplate](outputFrontendTemplate.md) - triggered when a front end template is printed to the screen
- [outputBackendTemplate](outputBackendTemplate.md) - triggered when a back end template is printed to the screen
