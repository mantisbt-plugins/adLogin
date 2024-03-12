
# 	adLogin Plugin

  - Version 2.01

## Copyright
  -  2024 Cas Nuy ( www.NUY.info )

## Description

This plugin allows for integrated login with AD credentials.
If you installed Mantis under IIS and want to have single signon with AD, all you need to do is the following: 
1. Disable Anonymous access for the Mantis website 
2. Ensure Integrated Windows Authentication is ticked 
Users listed in the user-table with their windows username, will be automatically logged on.
In all other cases the normnal Mantis login screen will appear.

## Requirements
    - Mantis 2.00
 
## Installation                                                                             
 
Like any other plugin. 

### To make it work

This plugin uses the function auth_attempt_script_login, which in the past was enough for getting access.
As of version 1.2.x this function offers less functionality than before.
This fuction is available in core\authentication_api.php
In order to overcome this, one needs to add 3 lines at the end of this function:
	- $p_perm_login=false;
	- auth_set_cookies( $t_user_id, $p_perm_login );
	- auth_set_tokens( $t_user_id );
	
Add these just before the comment line stating:
 - # ok, we're good to login now

In addition, one can uncomment the line:
	# user_increment_login_count( $t_user_id );
It should look like:
	user_increment_login_count( $t_user_id );
In that case still all logins are counted.	

### Disclaimer

The change mentioned above can bring additional security risks in case you Mantis is on the WWW opposite an intranet.

## Configuration options                                                                      
 
- None

## License                                                                                    

Released under the [GPL v3 license](http://opensource.org/licenses/GPL-3.0).

## Support

File bug reports and submit questions on the
[GitHub issues tracker](http://github.com/mantisbt-plugins/adLogin/issues).
