
Formatting date and time
========================

To manually format a timestamp you can use the `parseDate` method. 

You can define wheter you want to output days, weeks, hours, minutes etc and in which format. The formatting works according to [PHP's `date` function][1].

```php
<?php
// outputs date like this '30.05.2012'
echo $this->parseDate('d.m.Y', $this->time);
```

[1]: http://php.net/date    "Description of PHP Date function"
