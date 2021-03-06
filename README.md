# PHP7-CallManager-AXL
PHP Implementation to interface with Cisco unified call manager (CUCM) over the administrative XML (AXL) implememtation.
This library requires a copy of the CORRECT .WSDL file for YOUR VERSION of callmanager.
This library is under development so should be considered unstable and subject to major changes.

## Naming Convention

```
This library is dependent on a naming convention specific to the owner's environment. Use at your own risk. 

```

|Object Type|Example Name|
|------------------|--------------------|
|Route Group|RG_{$SITE}  |
|Media Resourse Group List|MRGL_{$SITE}  |
|Media Resourse Group|MRG_{$SITE}  |
|Media Terminiation Point|{$SITE}_711  |
|Media Terminiation Point|{$SITE}_729  |
|Conference Bridge|{$SITE}_CFB  |
|Device Pool|DP_{$SITE}  |
|Call Manager Group|CMG-{$SITE}  |
|Region|R_{$SITE}  |
|Location|LOC_{$SITE}  |
|Calling Search Space|CSS_{$SITE}  |
|Partition|PT_{$SITE}  |
|SRST |SRST_{$SITE}  |


## Install via Composer

```
composer require iahunter/php5-callmanager-axl
```
### Example - List Device Pool Names

```php
require_once "./vendor/autoload.php";                         

$URL    = "https://10.11.12.13:8443/axl"; // Prod CUCM           
$SCHEMA = "./axl/schema/10.5/AXLAPI.wsdl";                 
$USER   = "username";
$PASS   = "password";

try {
    $CUCM = new \Iahunter\CallmanagerAXL\Callmanager($URL, $SCHEMA, $USER, $PASS);
    
    $DP = $CUCM->get_device_pool_names();        
    print_r($DP);                                          

} catch (\Exception $E) {        
    echo "Error communicating with callmanager: {$E->getMessage()}".PHP_EOL;
}
```

### Example - List Phone Names

```php
require_once "./vendor/autoload.php";                         

$URL    = "https://10.11.12.13:8443/axl"; // Prod CUCM           
$SCHEMA = "./axl/schema/10.5/AXLAPI.wsdl";                 
$USER   = "username";
$PASS   = "password";

try {
    $CUCM = new \Iahunter\CallmanagerAXL\Callmanager($URL, $SCHEMA, $USER, $PASS);

    $PHONES = $CUCM->get_phone_names();        
    print_r($PHONES);                                          

} catch (\Exception $E) {        
    echo "Error communicating with callmanager: {$E->getMessage()}".PHP_EOL;
}
```
