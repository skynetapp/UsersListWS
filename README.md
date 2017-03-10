#### Date: 02-03-2017
#### Description: This module explains to get the users list using WS call.

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | UsersListWSConnection
Lib | Smarty,nusoap
Modules | UsersController, UsersAction, UsersView, UsersWS
Views | UsersViewForm

#### Architecture

- Upon running the url, we will be getting the users list information.
- First we will get the login session id and will set the ws client connection.
- Next we will get the users list array by passing parameters to ws call ** get_entry_list**.
- The array list we will be showing the output in a table.


#### Main Flow

- To get the list: index.php -> controller -> action -> UsersWS
- To display the list: controller -> action -> Usersview -> tpl (in views folder)

#### Step 1: 

- Based on the url **http://159.203.239.91/UsersListWS/index.php?module=Users&action=UserList** first we need to call module **Users** and the corresponding action **UserList** from index.php. 
- Function **UsersListFlow** will be executed first from index.php -> controller.
- Function **getUsersList** will be called from controller to action.
- Function **setWSDLHandle** will get the ws client connection from UsersWS.php and will get the login session id.
- Function **getUsersListArray** will be called in action from UsersWS.php which will get the parameters by ws call **get_entry_list** and returns the users result.

#### Step 2:

- The array result will be passed to function **showUsersList** from controller -> action.
- Function **showUsersListView** will be called from action -> usersview.php which is included in UsersAction.php
- The display tpl page will be called in UsersView.php which gives the output of users list. 

#### Steps to Execute:

- If we need to run the code , the below changes need to be done in config.php

 **_Code:_**
	
```
$GLOBALS['base_path'] = 'http://159.203.239.91/UsersListWS';
$GLOBALS['root_path'] = '/var/www/html/UsersListWS/';
```


#### Assumptions

- Not Applicable.

#### Errors

If any error found , then it might be the following reasons.

- If the url call is not right, the output will be blank page. It should be as below.

**_Url:_**
	
```
http://159.203.239.91/UsersListWS/index.php?module=Users&action=UserList
```
- The root path and base path in config.php might be wrong. It should be same as above in steps to execute.
- sugar username and password might not be correct in Global -> UsersListWSConnection.php.
- sugar url path may be wrong in Global -> UsersListWSConnection.php.
- If we are not getting the output, then ws call need to be checked. it should be as **get_entry_list**.


