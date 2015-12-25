deviantPHP
==========

Warning!
--------
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

Quickstart:
-----------
Having installed deviantPHP via Composer, you have the extra plus of autoloading. We define DeviantPHP as namespace, thus the main class is called \DeviantPHP\DeviantPHP.
Obviously, you will need to change CLIENT_ID, CLIENT_SECRET, THIS_URL AND SCOPES to suit your needs. Please see [Deviantart Developer](https://www.deviantart.com/developers/) for more information.

```PHP
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
  
```
Functions:
----------
The following table gives an overview of the actual functions. These are subject to change, that is, some functions may be added/removed in the future.

Function        | Arguments 		 					| Explanation
--------------- | --------- 		 					| -----------
__construct()   | $params (array)    					| The constructor accepts client_id, client_secret, redirect_uri, scope and user_agent as option.
authenticate    | none      		 					| Handles the OAuth flow. 
createAuthUrl   | none			     					| Returns the authentication URL needed for the OAuth flow.
getAccessToken  | $code (string)	 					| Get an access/refresh token from deviantart, needs the OAuth code as input.
refreshToken    | none			     					| Gets a new access token if the old one is expired (after one hour).
uploadFile      | $filename (string) 					| Uploads a file to sta.sh with the given name. Returns the result (file id) as associative array.
getUser         | none									| Get infos about the authorized user.
isAuthenticated | none 									| Checks if the access token is still valid. Returns true or false.
setRedirect		| $url (string) 						| Sets the redirect_uri (for OAuth).
getRedirect     | none 				 					| Returns the actual redirect_uri.
setToken 		| $access (string), $refresh (string)	| Sets the access and refresh tokens (these might come from a database/session)
getToken 		| none 									| Returns the tokens as an associative array (access_token, refresh_token).
setCredentials  | $credentials (array) 					| Sets the client_id and client_secret ($credentials = array("client_id" => "1234", "client_secret" => "secret")
getCredentials  | none 									| Returns the credentials as associative array.

Problems/Wishes
---------------
If you encounter any problems, please drop us a line at bot@boxconnect.org or make a pull request.
