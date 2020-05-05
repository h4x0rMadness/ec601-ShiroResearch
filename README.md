# EC601_MiniProject_2
EC601_MiniProject_2 on Cybersecurity

## Introduction

### What is Cybersecurity?

Cybersecurity is the protection of internet-connected systems, including hardware, software and data, from cyberattacks. The purpose of cybersecurity is to help prevent cyberattacks, data breaches and identity theft and can aid in risk management. Cybersecurity is challenged by many aspects of threats:

·Malware, any file or program used to harm a computer user, such as worms, computer viruses, Trojan horses and spyware.

·Ransomware, a subset of malware in which the data on a victim's computer is locked malware

·Social engineering, an attack that relies on human interaction to trick users into breaking security procedures in order to gain sensitive information that is typically protected.

·Phishing, a form of fraud where fraudulent emails are sent that resemble emails from reputable sources; however, the intention of these emails is to steal sensitive data, such as credit card or login information.

### What is Apache Shiro?
<p align="center">
 <img src="https://github.com/h4x0rMadness/EC601_MiniProject_2/blob/master/ShiroBasicArchitecture.png" width="50%">
</p>

Apache Shiro is a powerful and flexible open-source security framework that cleanly handles authentication, authorization, enterprise session management and cryptography.

<p align="center">
 <img src="https://github.com/h4x0rMadness/EC601_MiniProject_2/blob/master/ShiroFeatures.png" width="70%">
</p>

Authentication: Sometimes referred to as ‘login’, this is the act of proving a user is who they say they are. 

Authorization: The process of access control, i.e. determining ‘who’ has access to ‘what’. 

Session Management: Managing user-specific sessions, even in non-web or EJB applications. 

Cryptography: Keeping data secure using cryptographic algorithms while still being easy to use. 


<p align="center">
 <img src="https://github.com/h4x0rMadness/EC601_MiniProject_2/blob/master/ShiroArchitecture.png" width="70%">
</p>


#### Subject (org.apache.shiro.subject.Subject)

A security-specific ‘view’ of the entity (user, 3rd-party service, cron job, etc) currently interacting with the software.

#### SecurityManager (org.apache.shiro.mgt.SecurityManager)

As mentioned above, the SecurityManager is the heart of Shiro’s architecture. It is mostly an ‘umbrella’ object that coordinates its managed components to ensure they work smoothly together. It also manages Shiro’s view of every application user, so it knows how to perform security operations per user.

 #### Authenticator (org.apache.shiro.authc.Authenticator)
 
   The Authenticator is the component that is responsible for executing and reacting to authentication (log-in) attempts by users. When a user tries to log-in, that logic is executed by the Authenticator. The Authenticator knows how to coordinate with one or more Realms that store relevant user/account information. The data obtained from these Realms is used to verify the user’s identity to guarantee the user really is who they say they are.

 #### Authentication Strategy (org.apache.shiro.authc.pam.AuthenticationStrategy)
 
  If more than one Realm is configured, the AuthenticationStrategy will coordinate the Realms to determine the conditions under which an authentication attempt succeeds or fails (for example, if one realm succeeds but others fail, is the attempt successful? Must all realms succeed? Only the first?).

 #### Authorizer (org.apache.shiro.authz.Authorizer)
 
 The Authorizer is the component responsible determining users’ access control in the application. It is the mechanism that ultimately says if a user is allowed to do something or not. Like the Authenticator, the Authorizer also knows how to coordinate with multiple back-end data sources to access role and permission information. The Authorizer uses this information to determine exactly if a user is allowed to perform a given action.

#### SessionManager (org.apache.shiro.session.mgt.SessionManager)

 The SessionManager knows how to create and manage user Session lifecycles to provide a robust Session experience for users in all environments. This is a unique feature in the world of security frameworks - Shiro has the ability to natively manage user Sessions in any environment, even if there is no Web/Servlet or EJB container available. By default, Shiro will use an existing session mechanism if available, (e.g. Servlet Container), but if there isn’t one, such as in a standalone application or non-web environment, it will use its built-in enterprise session management to offer the same programming experience. The SessionDAO exists to allow any datasource to be used to persist sessions.

 #### SessionDAO (org.apache.shiro.session.mgt.eis.SessionDAO)
 
  The SessionDAO performs Session persistence (CRUD) operations on behalf of the SessionManager. This allows any data store to be plugged in to the Session Management infrastructure.

 #### CacheManager (org.apache.shiro.cache.CacheManager)
 
 The CacheManager creates and manages Cache instance lifecycles used by other Shiro components. Because Shiro can access many back-end data sources for authentication, authorization and session management, caching has always been a first-class architectural feature in the framework to improve performance while using these data sources. Any of the modern open-source and/or enterprise caching products can be plugged in to Shiro to provide a fast and efficient user-experience.

#### Cryptography (org.apache.shiro.crypto.*)

 Cryptography is a natural addition to an enterprise security framework. Shiro’s crypto package contains easy-to-use and understand representations of crytographic Ciphers, Hashes (aka digests) and different codec implementations. All of the classes in this package are carefully designed to be very easy to use and easy to understand. Anyone who has used Java’s native cryptography support knows it can be a challenging animal to tame. Shiro’s crypto APIs simplify the complicated Java mechanisms and make cryptography easy to use for normal mortal human beings.

#### Realms (org.apache.shiro.realm.Realm)

 As mentioned above, Realms act as the ‘bridge’ or ‘connector’ between Shiro and your application’s security data. When it comes time to actually interact with security-related data like user accounts to perform authentication (login) and authorization (access control), Shiro looks up many of these things from one or more Realms configured for an application. You can configure as many Realms as you need (usually one per data source) and Shiro will coordinate with them as necessary for both authentication and authorization.



###  What can you do with Apache Shiro?

Here are some things that you can do with Apache Shiro:

Authenticate a user to verify their identity

Perform access control for a user, such as:

  Determine if a user is assigned a certain security role or not
  
  Determine if a user is permitted to do something or not
  
  Use a Session API in any environment, even without web or EJB containers.
  
  React to events during authentication, access control, or during a session’s lifetime.
  
  Aggregate 1 or more data sources of user security data and present this all as a single composite user ‘view’.
  
  Enable ‘Remember Me’ services for user association without login
  …
  and much more - all integrated into API.


## Pros and Cons:

Pros: flexibility, easy to configure, supports cloud, desktop and mobile platform

Cons:Apache Shiro does not currently deal with Virtual Machine level security. Shiro does not currently natively support ‘multi-stage’ authentication

## Recommendations and Conclusion:

Apache Shiro seems to be a reliable, easy to understand framework to work with. It supports different platforms and works beautifully on different environments. Besides, Apache Shiro is easy to install and configure. However, if you work with VM and want to do cybersecurity protection, other options may be better choice.


## Reference:

https://searchsecurity.techtarget.com/definition/cybersecurity

Apache Shiro Document

https://shiro.apache.org/10-minute-tutorial.html

Security for Java Web Applications Using Apache Shiro - Javier Ochoa
