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

- If the action is **empty**, welcome page will be displayed.
- If the action is **login or signup**, it shows the login form.
- If the action is **corporate**, it shows the corporate form.
- If the action is **sendConformationCode**, it will first create object array for input data to login and will call the wsdl for getting admin login.
- If the admin login is success, convert array to object step will be executed and sends the confirmation code to user which redirects to password confirmation page.
