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

#### Main Flow

- To get the list: index.php -> controller -> action -> UsersWS
- To display the list: controller -> action -> Usersview -> tpl (in views folder)

#### Step 1: 

- Based on the url **http://159.203.239.91/UsersListWS/index.php?module=Users&action=UserList** first we need to call module **Users** and the corresponding action **UserList** from index.php. 
- Function **UsersListFlow** will be executed first from index.php -> controller.
- Function **getUsersList** will be called from controller to action.
- Function **setWSDLHandle** will get the ws client connection from UsersWS.php and will get the login session id.
- Function **getUsersListArray** from action will get the parameters by ws call **get_entry_list** and returns the users result.
- The array result will be passed to function **showUsersList** in controller.
