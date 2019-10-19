Java Authentication with Apache Shiro

Steps
Collect the subject’s principals and credentials
Submit the principals and credentials to an authentication system.
Allow access, retry authentication, or block access

Step 1 - Collect the subject’s principals and credentials
//Example using most common scenario: 
//String username and password.  Acquire in 
//system-specific manner (HTTP request, GUI, etc)
UsernamePasswordToken token = new UsernamePasswordToken( username, password );

//”Remember Me” built-in, just do this: 
token.setRememberMe(true);

In this particular case, we’re using a class called UsernamePasswordToken. It is the most common authentication token used in the framework.
We use this token to bundle the username and password we acquired in someway in our Java application. Maybe they were submitted via a user web form, an HTTP header, or a command line. In Shiro, it does not matter how you acquire them– it is protocol agnostic.
In this example, we have decided that we want the application to remember users when they return. So once the token is created, we use Shiro’s built-in “Remember-me” feature by setting it to true on the token. This is done using the token’s setRememberMe() method

Step 2 - Submit the principals and credentials to an authentication system.
So we’ve collected the information in a token and set it to remember returning users. The next step is in the Authentication process is to submit the token to an authentication system. 

//With most of Shiro, you'll always want to make sure you're working with the currently 
//executing user, referred to as the subject 
Subject currentUser = SecurityUtils.getSubject();

//Authenticate the subject by passing 
//the user name and password token 
//into the login method 
currentUser.login(token);


Now with the user representation in hand, we authenticate them by just calling the login()) method and submit the token we just constructed a second ago.

Step 3 - Allow access, retry authentication, or block access
Again really, really easy, single method call. If the login() method call is successful, then the user is logged in and associated with a user account or identity. From here, the user can go about using your application and retain their identity through their session or longer since we have set the “Remember Me” in our example.
What happens if something fails in the authentication attempt? What if they give you the wrong password or they accessed the system too many times, maybe their account is locked? In this case, Shiro will throw an exception. This is where Shiro’s rich exception hierarchy comes into play.
try {
    currentUser.login(token);
} catch  ( UnknownAccountException uae ) { ...
} catch  ( IncorrectCredentialsException ice ) { ...
} catch  ( LockedAccountException lae ) { ...
} catch  ( ExcessiveAttemptsException eae ) { ...
} ...  your own ...
} catch ( AuthenticationException ae ) {
    //unexpected error?
}
//No problems, show authenticated view…

Logging Out
Finally, when the user is done using the application, they can log out. And in Shiro, we make logging out quick and easy with a single method call.
currentUser.logout(); //removes all identifying information and invalidates their session too.
