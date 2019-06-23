## Installing Microsoft driver on MAMP PHP for MacOS i.e (PDO_SQLSRV & SQLSRV)  

> This is a guide on how you can install Microsoft SQL Driver on MAMP server on a MacOS for PHP


Have you ever tried communicating with Microsoft SQL serves in PHP?  
You would have noticed it is a lot of a hassle. At first i tried it on a windows system using PHP XAMP.  
All i did was to download the drivers from [Microsoft Drivers for PHP for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=57916) then unzip the file or run the **.exe** file to unzip the driver, after that i copied the needed drivers e.g **(php_sqlsrv_72_ts.dll & php_pdo_sqlsrv_72_ts.dll)** to the **c:\XAMPP\PHP\ext** folder then opened the **php.ini** file and added the following line to the the file:  

`extension=php_sqlsrv_72_ts.dll`  
`extension=php_pdo_sqlsrv_72_ts.dll`  

After adding the above to the **php.ini** file i saved it and restarted my Apache server and that was all, i confirmed by going to **phpinfo.php** page on the xampp localhost admin page and <code>command + F</code> to find anything relating to **sqlsrv**.  


> Whew!, Thats a whole lot of information at a go.  


### Now lets get to installing the same driver on PHP on MAMP for MacOS.  


Now i assume you have your MAMP installed successfully.  
If you don't have MAMP installed kindly goto [MAMP & MAMP PRO](https://www.mamp.info/en/downloads/) to get it installed.  
If you have MAMP installed successfully you can follow this steps.  

**1. STEP ONE: Install Brew**  
If you don't have Brew installed, open terminal and run:  

`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`  

The above instruction would install Brew. next run:  

`brew tap`  
`brew tap homebrew/core`

**2. STEP TWO: Use MAMP's version of PHP instead of the default on OSX**  
Next, we have to make the default php on OSX use that of MAMP, to get the version the default php used by your MAMP:  
- Open your MAMP windown  
- Click on MAMP on the menu bar  
- Click on Preference or use the keyboard shortcut `command + ,`
- Click on the **PHP** tab.

**N:B** note the select PHP version.  
Next open teminal and run:

 <code>PHP_VERSION=&#96;ls /Applications/MAMP/bin/php/ | sort -n | tail -1&#96;</code>  
 `export PATH=/Applications/MAMP/bin/php/${PHP_VERSION}/bin:$PATH`  
 e.g assuming php version is 7.3.1  
 `export PATH=/Applications/MAMP/bin/php/php7.3.1/bin:$PATH`  





