deviantPHP
==========

Warning!
--------------
**First of all**: This is not an official package from http://deviantart.com.  
It is a wrapper for some of theirs functions and hooks because we needed some sort of library for our project http://boxconnect.org. That said, let's see, how we can help nevertheless.

Installation
------------
The simplest way to install the package, is via [composer](https://getcomposer.org/). Otherwise, just include() the deviantPHP.php file in the folder /src.

	{
 		"require": {
			"boxconnect/deviant-php": "dev-master" 
		}
	}	

Usage/Functions:
----------------
Having installed deviantPHP via Composer, you have the extra plus of autoloading. We define DeviantPHP as namespace, thus the main class is called \DeviantPHP\DeviantPHP.
Obviously, you will need to change CLIENT_ID, CLIENT_SECRET, THIS_URL AND SCOPES to suit your needs. Please see [Deviantart Developer](https://www.deviantart.com/developers/) for more information.

	<?php
	require_once "vendor/autoload.php";

	use \DeviantPHP as dvp;
	$options = array("client_id" => CLIENT_ID, 
					"client_secret" => CLIENT_SECRET,
					"redirect_uri" => THIS_URL,
					"scope" => SCOPES);

	$dvpClient = new dvp\DeviantPHP($options);
	$dvpClient->authenticate();
	if ($dvpClient->isAuthenticated())
		$dvpClient->uploadFile(SOME_FILE);

	?>
