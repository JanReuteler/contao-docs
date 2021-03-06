outputBackendTemplate
---------------------

The `outputBackendTemplate` hook is triggered when a back end template is printed to the screen. It passes the template content and the template name as arguments and expects the template content as return value. It is available from version 2.6.0.


### Parameters ###

1. *string* `$strContent`

	Content of the rendered backend template.

2. *string* `$strTemplate`

	The template name (e.g. `be_main`) without file extension.


### Example ###

```php
<?php

// config.php
$GLOBALS['TL_HOOKS']['outputBackendTemplate'][] = array('MyClass', 'myOutputBackendTemplate');

// MyClass.php
public function myOutputBackendTemplate($strContent, $strTemplate)
{
    if ($strTemplate == 'be_main')
    {
        // Modify output
    }

    return $strContent;
}
```


### See Also ###

- [outputFrontendTemplate](outputFrontendTemplate.md) - triggered when a front end template is printed to the screen
- [parseBackendTemplate](parseBackendTemplate.md) - triggered when a back end template is parsed
- [parseFrontendTemplate](parseFrontendTemplate.md) - triggered when a front end template is parsed
