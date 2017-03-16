#### Date: 16/03/2017

#### Description: This document explains the code flow of login .

#### The Folder Structure is as follows:

 Root Directory | Sub Directory 
------------ | -------------
index.php | 
Global | LytepoleWSConnection
Lib | Smarty,nusoap
Modules | Login
Views | login_signup, loginForm, loginFormCorporate, passwordVerificationForm


#### Architecture

The login process will be based on the action redirection will be executed.

- If the action is **empty**, welcome page will be displayed by function **displayWelcomeForm**.
- If the action is **login or signup**, it shows the login form by function **displayLoginForm**.
- If the action is **corporate**, it shows the corporate form by function **displayCorporateLoginForm**.
- If the action is **sendConformationCode**, first it will create object array for input data by function **createLoginVO** to login and will call the wsdl for getting admin login by function adminLogin.
- If the admin login is success, convert array to object step will be executed by calling function **covertArrayToObject** and sends the confirmation code to user by function **sendVerificationCode** which redirects to password confirmation page by calling function **displayPasswordVerificationView**.

- Action -> **ProcessLogin** is executed once user enter conformation for process login. First it will create object array for input data by function **createLoginVO** to login and will call the wsdl for getting admin login by function adminLogin.
- If the admin login is success, convert array to object step will be executed by calling function **covertArrayToObject** and checks the login password by function **processLoginFunctionality** which redirects header location to landing page.
- If the password is incorrect it will show error and reidrect to login page by calling function **displayPasswordVerificationView**.

- If If action is **logout or sign out**, it will set the session id and will redirect to index page .
- If action is **Resendcode** , it resends password to user by calling function **Resendcode**.
