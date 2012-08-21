
Formatting numbers
==================


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
