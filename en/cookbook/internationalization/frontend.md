
## Frontend-Labels

The labels in the frontend are simple. Most of the time they are stored in the associated language file of the given table. In this example it's the 'apartment' table.

___

### Labels for DCA-defined-fields

The mapping between the field and the label is usually done with the field-key that was given in the DCA definition of said table.



**Example:** 

/propertymanager/languages/en/tl\_apartment.php
```php
<?php

/**
 * Fields
 */
$GLOBALS['TL_LANG']['tl_apartment']['price']			= array('Price', 'Please enter the price.');
$GLOBALS['TL_LANG']['tl_apartment']['additionalCosts']	= array('Additional costs', 'Please enter the additional costs');

// ...

?>
```

---

### Custom-Labels

In case you wish to have additional labels defined in a language-file you can easily do so by writing something like the code below. 

It doesn't have to be the 'custom_label'-key, you can choose whatever you want, but I suggest you group them in their own array:

```php
<?php

/**
 * Fields
 */

// custom labels 

$GLOBALS['TL_LANG']['tl_apartment']['custom_label']['icon_alt']	= 'This is the alternative text of an image';
$GLOBALS['TL_LANG']['tl_apartment']['custom_label']['label1']	= 'This is a label that can be used for whatever you want';

// ...

?>
```
To use those in a template, I suggest you do the following in the module/content element: 

```php
<?php
	$this->Template->custom_labels = $GLOBALS['TL_LANG']['tl_apartment']['custom_label'];
?>
```
In the template they can then be accessed like this.
<?php echo $this->icon_alt; ?> and <?php echo $this->label1; ?> 

**Note:** Make sure the language file is loaded (see below).

---


Sometimes you might want to use a specific language file. To load any language file manually, use the following. In this case it's the language file 'tl_apartment.php' from the examples above:

```php
<?php
	$this->loadLanguageFile('tl_apartment');
?>
```


It doesn't have to be the label-file of a table, in case you had a */languages/en/various\_labels.php* and wanted to use it, do this:
```php
<?php
	$this->loadLanguageFile('various_labels');
?>
```

**Note:** For 'loadLanguageFile' to work, the language files must be part of the same module:

### Formatting timestamps

To manually format a timestamp you can use the 'parseDate' method. 

You can define whet ever you want to output days, weeks, hours, minutes etc and in which format. On the following link you find the allowed list of parameters: http://ch2.php.net/manual/de/function.date.php
```php
<?php
	echo $this->parseDate("d.m.Y", $this->time); // outputs date like this '30.05.2012'
?>
```

### Formatting numbers


#### Changing decimals using Contao settings 
If you want to limit the decimals of a given number you can do this with the 'getFormattedNumber' method. 

**Note:** The number will be formatted using the defined Contao settings for decimal- and -thousands-separator.

```php
<?php
	$strNumber = "124.3333333333333";
	echo $this->getFormattedNumber($varNumber, 2); // outputs the number like this '124.33'
?>
```

#### Advanced number formatting

If you want to format a number without using the global decimal- and thousands-separator settings from Contao you can do this too.


```php
<?php
	$strNumber = "124.3333333333333";
 	$intDecimals = 4;
 	
 	$decimalSeparator = ','; // Contao default value: $GLOBALS['TL_LANG']['MSC'] ['decimalSeparator']
 	$thousandsSeparator = ''; // Contao default value: $GLOBALS['TL_LANG']['MSC']['thousandsSeparator']
 
 	echo number_format(round($varNumber, $intDecimals), $intDecimals, $decimalSeparator, $thousandsSeparator); // outputs the number like this '124,3333'
?>
``` 
