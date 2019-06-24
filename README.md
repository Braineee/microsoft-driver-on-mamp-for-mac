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

Next, we have to make the default php on OSX use that of MAMP, to get the default version of php used by your MAMP:  
- Open your MAMP window  
- Click on MAMP on the menu bar  
- Click on Preference or use the keyboard shortcut `command + ,`
- Click on the **PHP** tab.

**N:B** note the selected PHP version.  
Next open teminal and run:

<code>PHP_VERSION=&#96;ls /Applications/MAMP/bin/php/ | sort -n | tail -1&#96;</code>  
`export PATH=/Applications/MAMP/bin/php/${PHP_VERSION}/bin:$PATH`  

e.g assuming php version is 7.3.1  

`export PATH=/Applications/MAMP/bin/php/php7.3.1/bin:$PATH`  

In order to verify that the operation was successfull, lets check the PHP version on the terminal by running the following command:  

<code>php -v</code>  

You should now see the the same php version on your MAMP on your terminal also.  



**3. STEP THREE: Install prerequisites (Microsoft ODBC Driver 17 for SQL Server)**  

Next, we have to install the prerequsites for the driver by running the following code:  

`brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release`  
`brew update`  
`brew install msodbcsql17 mssql-tools`  

In addition, you may need to install the GNU make tools by running:  

`brew install autoconf automake libtool`  



**4. STEP FOUR: Install the PHP drivers for Microsoft SQL Server**  

Next, we proceed to installing the PHP drivers i.e **pdo_sqlsrv.so & sqlsrv.so**:  

First, we navigate to the php version file in mamp  

`cd /Applications/MAMP/bin/php/${PHP_VERSION}/bin`  

e.g assuming php version is 7.3.1  

`cd /Applications/MAMP/bin/php/php7.3.1/bin`  

Next, we download the drivers by running:  

`sudo pecl install sqlsrv`  
`sudo pecl install pdo_sqlsrv`  

> Downloading the drivers might take some time  

After the download is complete, we then have to add the name of the newly installed driver extention to the **php.ini** file to complete the installation process.  

> this would be stated on the terminal at the end of the download of the drivers.

to complete the installation:

- Copy the downloaded driver extension name on the terminal i.e `extension=pdo_sqlsrv.so & extension=sqlsrv.so`.
- Navigate to **/Applications/MAMP/bin/php/${PHP_VERSION}/config/** on finder.
- Open the **php.ini** file with any text editor.
- Use the keyboard shortcut `command + F` to search for the word extension.
- Paste the copied driver extension names below the listed extension.
- Use the keyboard shortcut `command + S` to save the file and then close the file.
- Finally restart the MAMP in order to restart the Apache server.  

In order to verify if the installation was successfull, Open the MAMP localhost page on the browser.

> The localhost page shold automatically be open on a browser when you restart MAMP  

Click on the `php info` link to get to the phpinfo.php page.  

Use the keyboard shortcut `command + F` to search for the word *'sqlsrv'* you should now see the sqlsrv extentions pop up on the page. and you are done.  

***

### For reference purpose you can visit.  

- [Installation Tutorial for the Microsoft Drivers for PHP for SQL Server](https://docs.microsoft.com/en-us/sql/connect/php/installation-tutorial-linux-mac?view=sql-server-2017).  

- [Installing the Microsoft ODBC Driver for SQL Server on Linux and macOS](https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017).  

- [How to override the path of PHP to use the MAMP path](https://stackoverflow.com/questions/4145667/how-to-override-the-path-of-php-to-use-the-mamp-path).

- [Installation Tutorial for the Microsoft Drivers for PHP for SQL Server - video tutorial](https://www.youtube.com/watch?v=PRH04PxZpUk).


Made with love from David:

[twitter @alindavidsin02](https://twitter.com/alindavidsin02).  










