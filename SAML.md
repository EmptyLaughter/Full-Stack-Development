# SAML - Security Assertion Markup Language
### Condensed notes from tutorials for self use

## Why SAML
* "Secure xml-based communication mechanism for communicating identities between organizations"
* Internet Single Sign-On
    * Increases security - eliminates need to have credentials in multiple locations
    * Increases access - signed on to one, signed on to all
* Eliminate admin time and cost

## SAML Flow: IdP and SP
* **Identity Provider (IdP)**: organization that maintains list of users and way to authenticate
* **Service Provider (SP)**: Hosts application

A user will try to access an application. The application (SP) will get the origanization (IdP) to validate user identity. IdP will tell SP things are a go, which then creates a session for the user. The user will be pleased with the invisible magic that goes on behind the scenes.

## Configuring Python Toolkit
1. src directory: python-saml-master/src/one/login/saml2
    **place holder text here**

2. demo-flask directory: 
    
    > ls demo-flask
    index.py    requirements.txt    saml    templates
    

    index.py: main flask file
    
    templates directory: pretty templates for visuals
    
    requirements.txt: states flask version needed

    saml directory:
    
    > ls saml
    advanced_settings.json    certs    settings.json
    

    advanced_settings.json: stores security settings
        * "security" and "signMetadata" hold signatures and encryptions required
        * "contactPerson": who to contact when things go wrong
        * "organization": organization info

    certs: stores x509 public and private key

    settings.json: stores SP and IdP information

        * set "strict" to true

        * "sp"
            * "entityId": SP URI
            
            * "assertionConsumerService": json object tells where and how authentication response message is returned to SP
            
                * "url": URL where response from IdP will be returned
                
                * "binding": SAML protocol binding; only HTTP-POST binding
                
        * "attributeConsumingService"
        
            * (optional) json object for requested attributes
        * "singleLogoutService"
        
            * json object that tells where and how logout response message is returned to SP

            * "url": URL where response from IdP will be returned

            * "binding: SAML protocol binding; only HTTP-Redirect binding

        * "NameIDFormat
            * choose format from python-saml-master/src/one/login/saml2/constants.py

        * "x509cert" and "privateKey" should be placed in certs folder and never published for others to see

        * "idp"

            * "entityId": IdP URI

            * "singleSignOnService"
            
                * "url": URL where authentication request message will be sent to IdP
                
                * "binding": SAML protocol binding; only HTTP-Redirect binding
            
        * "singleLogoutService
    
            * "url": IdP location where single logout request (slo) will be sent
    
            * "binding": SAML protocol binding; only HTTP-Redirect binding

        * "x509cert": public x509 certificate of IdP; can use a fingerprint (look at github onelogin documentation for more info about fingerprinting)

        * "x509certMulti": in the case that IdP uses different certificates for signing/encryption

3. Talk to IdP IT guy to get info that IdP expects and SP requirements

4. setup.py: setup information-- confirm and decide how to integrate with own application's setup.py

5. tests directory: unit tests that show that the toolkit-- should self inspect and run


## Sources
* Overview: https://developers.onelogin.com/saml
* SAML intro: https://www.youtube.com/watch?v=0fmNoqz6Urw
* Python toolkit and instructions: https://developers.onelogin.com/saml/python
* Python toolkit documentation: https://github.com/onelogin/python-saml
