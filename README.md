# Installing Microsoft driver on MAMP for MacOS (i.e, PDO_SQLSRV & SQLSRV) 

> This is a guide on how you can install Microsoft SQL Driver on MAMP server on a MacOS for PHP (PDO_sqlsrv &amp; sqlsrv))

Have you ever tried communicating with Microsoft SQL serves in PHP?  
You would have noticed it is a lot of a hassle. At first i tried it on a windows system using PHP XAMP, all i did was to download the drivers from [Microsoft Drivers for PHP for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=57916) then unzip the file or run the **.exe** file to unzip the driver, after that i copied the needed drivers e.g **(php_sqlsrv_72_ts.dll & php_pdo_sqlsrv_72_ts.dll)** to the **c:\XAMPP\PHP\ext** folder then opened the *php.ini* file and added the following line to the the file:  

`extension=php_sqlsrv_72_ts.dll`  
`extension=php_pdo_sqlsrv_72_ts.dll`  

After adding the above to the **php.ini** file i saved it and restarted my Apache server and that was all, i confirmed by going to **phpinfo.php** page on the xampp localhost admin page and <code>ctrl + F</code> to find anything relating to **sqlsrv**.

