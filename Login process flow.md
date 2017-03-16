
Function **processFlow** will be called from index.php to controller. This function is the first and main function in application. In this function the main parameter is action because based on that action we process all the redirections and processes

#### Step 1: 

Check the action parameter(login,signup,corporate,sendConformationCode,ProcessLogin,Logout,Signout,Resendcode).

-  If **action = empty** it shows the welcome form by function **displayWelcomeForm**.
- The function will display the tpl page as **login_signup.tpl** in views folder.

#### Step 2:

- If **action = login or signup** shows the login form by function **displayLoginForm**.
- The function will display the tpl page as **loginForm.tpl** in views folder.

#### Step 3:

- If **action = corporate** shows the corporate login form by function **displayCorporateLoginForm**.
- The function will display the tpl page as **loginFormCorporate.tpl** in views folder.

#### Step 4:

-  If **action = sendConformationCode** will be executed to send verfication code to his mobile.
- From controller to action, function **createLoginVO** is used to set the parameters for login like country code,number password etc.
- Result returns to controller.

- Function **adminLogin** takes the input value object and passes to the wsdl call to admin login.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **adminLogin** in LoginWS.php is used for admin login.
- Creating parameters for wsdl using object.
- Result returns the session id.

- If admin login is success, function **covertArrayToObject** is used to convert the array to object and set the values.
- Function **sendVerificationCode** takes the input value object and passes to the wsdl call to send password to the user.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **checkUserNameExists** in LoginWS.php will check whether user exist or not. 
- Creating the parameters and calling the wsdl call **get_entry_list** which returns the user id.
- Function **covertArrayToObject** in LoginData.php which is used to convert the array to object and set the values and will get the result count by **getResultCount** in action.

- If the result is 0, function **createNewUserDevice** will be called in action which is used to create new user device id .
- The wsdl call will be **set_entry_user_devices** which returns the result as device id to action.

- If the result is 1, it sets the user id, resend code and entry list id and calls the function **updateUserDevices** is used to update user devices.
- will call the wsdl call **set_entry_user_devices** and pass the created parameters to it which returns the device id.
- If the result is true, function **displayPasswordVerificationView** will display the password verifiaction tpl page.
- The tpl page will be **passwordVerificationForm.tpl** in views folder.



#### Step 5:

- If **action == ProcessLogin**, From controller to action, function **createLoginVO** is used to set the parameters for login like country code,number password etc.
- Result returns to controller.
- Function **covertArrayToObject** in LoginData.php which is used to convert the array to object and set the values and will get the result count by **getResultCount** in action.

- Function **processLoginFunctionality** takes the input value object and passes to the wsdl call to login and checked the password and redirects to the landing page.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **checkCorporateUserNameExists** is used to check whether corporate user exist or not.
- Will create parameters for wsdl using object and passing parameters to wsdl call **get_entry_list**.
- Result returns the code.
- If the result is true, the header will be redirected to landing page.
- If the password is not correct, function **displayPasswordVerificationView** will be called from controller to views and displays the tpl page.
- The tpl page will be **passwordVerificationForm.tpl** in views folder.


#### Step 6:

- If **action == Logout**, function **createLogoutVO** is used to logout from application.
- In action, above function sets the login session id and returns the result to controller.

- Function **logout** takes the input value object and passes to the wsdl call to logout.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **logout** in LoginWS.php is used for logout. 
- Will create the parameters for wsdl using object and pass the parameters to wsdl call **logout**.
- Result returns the session id and header location will be redirected to index.php.


#### Step 7:

- If **action == signout**, function **createLogoutVO** is used to logout from application.
- In action, above function sets the login session id and returns the result to controller.

- Function **logout** takes the input value object and passes to the wsdl call to logout.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **logout** in LoginWS.php is used for logout. 
- Will create the parameters for wsdl using object and pass the parameters to wsdl call **logout**.
- Result returns the session id and header location will be redirected to index.php.


#### Step 8:

- If **action == Resendcode**, function **Resendcode** which takes the input value object and passes to the wsdl call to send password code.
- In action, first wsdl client connection will be set by calling function **setWSClient**.
- Function **Resendcode** in LoginWS.php is used to resend the password code.
- The wsdl call used is **login** which returns the password code.














