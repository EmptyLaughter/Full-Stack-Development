# SAML - Security Assertion Markup Language

## Why SAML
* "Secure xml-based communication mechanism for communicating identities between organizations"
* Internet Single Sign-On
    * Increases security - eliminates need to have credentials in multiple locations
    * Increases access - signed on to one, signed on to all
* Eliminate admin time and cost

## SAML Flow: IdP and SP
* **Identity Provider (IdP)**: organization that maintains list of users and way to authenticate
* **Service Provider (SP)**: Hosts application

A user will try to access an application. The application (SP) will get IdP to validate user identity. IdP will tell SP things are a go, which then creates a session for the user.

## Sources
* Overview: https://developers.onelogin.com/saml
* SAML intro: https://www.youtube.com/watch?v=0fmNoqz6Urw
* Python toolkit and instructions: https://developers.onelogin.com/saml/python
* Python toolkit documentation: https://github.com/onelogin/python-saml
