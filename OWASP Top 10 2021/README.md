# OWASP Top 10 - 2021

## Introduction
    OWASP stands for "Open Web Application Security Project". As the name suggests it is useful in securing various web application. OWASP Top 10 document maps top 10 vulenerabilities found in web applications. 
    
    It represents a broad consensus about the most critical security risks to web applications. Both developers and testers can use this document to ensure the web application is secured.

## Top 10:2021 List
    A01 Broken Access Control
    A02 Cryptographic Failures
    A03 Injection
    A04 Insecure Design
    A05 Security Misconfiguration
    A06 Vulnerable and Outdated Components
    A07 Identification and Authentication Failures
    A08 Software and Data Integrity Failures
    A09 Security Logging and Monitoring Failures
    A10 Server Side Request Forgery (SSRF)

## A01 Broken Access Control
    Violation of least privilege or deny by default
    Bypassing login functionality
    Improper implementation of login, logout, register and forgot password 
    Accessing other accounts by changing unique Identifier in URL or any type of requests  
    Unrestricted use of APIs

## A02 Cryptographic Failures
    Transmitting or storing password in clear text
    Use of any weak cryptographic algorithm
    Not forcing HTTPS instead of HTTP
    Errors in SSL cert
    Are deprecated hash functions used like MD5 or SHA1

## A03 Injection
    Any sort of injection like command injection, SQL Injection or XSS
    Improper use of input or lack of input sanitization

## A04 Insecure Design
    Any logical gaps in software or web applications
    User enumeration by login, register or forget password
    Permitting weak passwords

## A05 Security Misconfiguration
    Using default configurations
    Using old and unpatched system settings / configuration
    Security headers not set
    Default credentials still in system
    Unnecessary features or ports active
    Old unused accounts still active

## A06 Vulnerable and Outdated Components
    Using vulnerable or old and unpatched softwares
    Not scanning for vulnerabilities regurarly
    Uncompatibile softwares, libraries used

## A07 Identification and Authentication Failures
    Permits automated attacks
    Permits brute forcing
    Default credentials still active
    Reusing session IDs
    Permitting guessable session IDs

## A08 Software and Data Integrity Failures
    Using digital signatures or hashing to make sure the data or softwares used are unaltered
    Only use softwares and libraries from trusted sources
    Not verifying updates

## A09 Security Logging and Monitoring Failures
    Failed login attempts not logged
    No backup of logs
    Not blocking brute force attacks
    Automated tools does not trigger alerts
    Over use of system resources does not trigger alert

## A10 Server Side Request Forgery (SSRF)
    It is a web security vulnerability that allows an attacker to induce the server-side application to make HTTP requests to an arbitrary domain of the attacker's choosing
    The attacker might cause the server to make a connection to internal-only services within the organization's infrastructure. In other cases, they may be able to force the server to connect to arbitrary external systems, potentially leaking sensitive data such as authorization credentials