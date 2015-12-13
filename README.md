# BasicAuth
The Code igniter library for basi authetication

This is a PHP Library/Class that can do basic user authentication. It assumes that the user identifier(s) and the password 
belong to the same table. 

You can have more than one user identifier i.e. name, username, emali... 
AND can have multiple password identifier column i.e passowrd, encrypted_code etc...

You can auto load the library in the autoload.php for access the class by
$this->load->library('basicauth');

The first thing you should do is set the table name, identifier columns and password columns. 
You can either change the basicauth.php file direcly OR use the setter functions 
BasicAuth::setIdentifierColumns(), BasicAuth::setPasswordColumns(), BasicAuth::setAuthTable() to set the variables.

The main function for authentication is BasicAuth::authenticate() which requires an associative array.

Example:
```
BasicAuth::setAuthTable('user');
BasicAuth::setIdentiferColumns(array('username', 'email'));
BasicAuth::setPasswordColumns(array('password'));
BasicAuth::authenticate(array('username' => 'me', 
                              'email' => 'me@me.com', 
                              'password' => 'secret....'));
```
Note:
The class uses a function encrypt() to encrypt the password before checking it with the user identifiers. 
You can change this function directly inside the class to put your own encrypting mechanism. By default it uses sha1()

There are two static functions BasicAuth::_preAuthenticate() and BasicAuth::_postAuthenticate() that you can use
to put your own logic before and the after the actual user authtication is done...

