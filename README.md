cgminerPHP
==========

A class made to help fetch API data from a cgminer client in PHP.

Commands
----------
For an updated list of cgminer commands, visit the [repo](https://github.com/ckolivas/cgminer/blob/master/API-README).

Initiation
----------
```php
require_once("class.cgminer.php");
$rig_info = new cgminerPHP("localhost", 4028);
```

Fetching Data
----------
```php
$rig_summary = $rig_info->request("summary");
print_r($rig_summary);
```

Examples
----------
These outputs are only a fraction of what the API offers. Examine the responses using ```print_r``` to find all the data received.


###### Fetching rig uptime and hashrate:
```php
$rig_summary = $rig_info->request("summary");
$uptime = $rig_summary["SUMMARY"]["Elapsed"];
$hashrate = $rig_summary["SUMMARY"]["Work Utility"];

echo gmdate("H:i:s", $uptime);
echo "<br>";
echo $hashrate;
```

###### Getting GPU info:
```php
$rig_gpu = $rig_info->request("gpu|0");
$temperature = $rig_gpu["GPU0"]["Temperature"];
$fan_speed = $rig_gpu["GPU0"]["Fan Speed"];
$fan_percent = $rig_gpu["GPU0"]["Fan Percent"];
```