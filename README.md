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
  
  This algorithm was published as RFC4226 by the Internet Engineering Task Force (IETF).it relies on two pieces of information. The first is the secret key, called the "seed", which is known only by the token and the server that validates submitted OTP codes. The second piece of information is the moving factor which, in event-based OTP, is a counter. The counter is stored in the token and on the server. The counter in the token increments when the button on the token is pressed, while the counter on the server is incremented only when an OTP is successfully validated.
  
  To calculate an OTP the token feeds the counter into the HMAC algorithm using the token seed as the key. HOTP uses the SHA-1 hash function in the HMAC. This produces a 160-bit value which is then reduced down to the 6 (or 8) decimal digits displayed by the token.
  
  ```
     hmacHash = HMAC-SHA-1(secretKey, counter);
     truncatedHash = (hmacHash[offset++] & 0x7f) << 24 | (hmacHash[offset++] & 0xff) << 16 | (hmacHash[offset++] & 0xff) << 8 |      (hmacHashh[offset++] & 0xff);
     finalOTP = (truncatedHash % (10 ^ numberOfDigitsRequiredInOTP));
  ```
## Question
  ### How to keep track of the counter?
  The solution is found in the TOTP.
  
## TOTP: Time-Based One-Time Password Algorithm
  A TOTP uses the HOTP algorithm to obtain the one time password. The only difference is that it uses “Time” in the place of “counter,” and that gives the solution to our problem.
  
  That means that instead of initializing the counter and keeping track of it, we can use time as a counter in the HOTP algorithm to obtain the OTP. As a server and phone both have access to time, neither of them has to keep track of the counter. To avoid the problem of different time zones of the server and phone, we can use a Unix timestamp, which is independent of time zones.

  So, TOTP uses time in increments called the timestep, which is usually 30 or 60 seconds. This means that each OTP is valid for the duration of the timestep.

  In this [link](https://asecuritysite.com/encryption/totp) your code will change each 5 seconds, you can try it.

  TOTP uses the HOTP algorithm, substituting the counter with a non-decreasing value based on the current time.
  
 ```
     T = an interval which will be used to calculate the value of the counter CT (default is 30 seconds) 
     counter = currentUnixTime / T
     TOTP value(K) = HOTP value(K, counter)
```
