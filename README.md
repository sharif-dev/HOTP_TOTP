# HOTP_TOTP
## What is Two Factor Authentication?
Two-factor authentication (or multi factor authentication) is just an extra layer of security for a user’s account. That means that, after enabling two factor authentication, the user has to go through one more step to log in successfully. This a process that gives web services secondary access to the account owner (you) in order to verify a login attempt. Typically, this involves a phone number and /or an email address. This is how it works: when you log into a service, you use your mobile phone to verify your identity by either clicking on a texted / emailed link, or by typing in a number sent by an authenticator app.  
FreeOTP is a two-factor authentication application for systems utilizing one-time password protocols.It provides implementations of HOTP and TOTP.Tokens can be added by scanning a QR code or by manually entering in the token configuration.FreeOTP implements open standards: HOTP and TOTP.
## HOTP( An HMAC-Based One-Time Password Algorithm)
It is a one-time password (OTP) algorithm based on hash-based message authentication codes (HMAC).

- One-time password(OTP)
 
  It is also known as one-time pin or dynamic password, is an automatically generated numeric or alphanumeric string of characters that authenticates the user for a single transaction or login session.An OTP is The Open Authentication Reference Architecture (OATH) initiative is a group of companies working together to help drive the adoption of open strong authentication technology across all networks.more secure than a static password, especially a user-created password, which can be weak and/or reused across multiple accounts.

- Hash-based message authentication codes(HMAC)

  Hash-based message authentication codes (or HMACs) are a tool for calculating message authentication codes using a cryptographic hash function coupled with a secret key. You can use an HMAC to verify both the integrity and authenticity of a message.
  
  Thease links( [link](https://cryptography.io/en/latest/hazmat/primitives/mac/hmac/),[link](https://asecuritysite.com/encryption/hotp)) will help.
