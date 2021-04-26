# 2FA Hackathon
Disclaimer: This hackathon will be organised by @arianvp  on personal initiative and 20% time. For now this document
is no active indication of any concrete roadmap by the company. Results of this hackathon are not an official Wire product at this point.

The goal of this hackathon is to research and explore secure methods of two-factor authentication that fit with Wire's goal to protect Digital Assets and promote [Zero Trust](https://gcn.com/articles/2020/04/20/zero-trust-infrastructure.aspx)

Two methods of authentication will be explored.  TOTP codes and https://www.w3.org/TR/webauthn/

TOTP codes are widely deployed and can be used with any phone that has Google Authenticator or similar installed.
It works by temporary time-based codes that need to be entered on login. Downside of TOTP codes is that they're not resistent to sophisticated phishing attacks.

FIDO2/Webauthn is a standard for authentiating with public key cryptography. Keys can be backed by platform or cross-platform authenticators. Meaning either the authenticator is built in to your device (Windows Hello, Apple TouchID, Apple FaceID, Android Fingerprint) or it can be a separate dongle (like a Yubikey).

It can be used for both passwordless authentication and two factor authentication usecases. Though we'll focus on
Two factor for now.


## Why?

* 2Fa is one of our most requested features https://github.com/wireapp/wire/issues/85
* Specifically people have been asking for Webauthn support given it is a widely-deployed standard in browsers now https://github.com/wireapp/wire/issues/85#issuecomment-481196915 https://github.com/wireapp/wire-webapp/issues/446#issuecomment-366453525
* According to Microsoft 2FA reduces 99.9% of attacks on accounts https://www.microsoft.com/security/blog/2019/08/20/one-simple-action-you-can-take-to-prevent-99-9-percent-of-account-attacks/
* According to Google hardware tokens made their company more secure and completely removed succesful phishing attacks https://research.google/pubs/pub45409/
* Unlike TOTP, FIDO2 makes phishing attacks cryptographically impossible
* Though we offer SSO support, and this has been our way to roll out 2FA to teams customers, team admins will still want heightend protection of their accounts. Security is only as strong as its weakest link

## The plan
@arianvp has been working quietly on the backend side of things in https://github.com/arianvp/haskell-fido2 
Once this library is ready for use and integrated with https://github.com/wireapp/wire-server he would love to organise
a hackathon with (one of) the client teams to do an end-to-end implementation of both TOTP and FIDO2/Webauthn support.
a good candidate would probably be the Web team, as webauthn support is directly built into browsers. 

For now however, plan is to keep working on the backend libraries for this as this is still in early stage.
This place serves as a collection of notes on 2FA support for myself

## Testing and debugging tools
* https://webauthn.io
* https://webauthn.me
* https://github.com/google/virtual-authenticators-tab

## Guides & Tutorials
* https://webauthn.guide
* https://github.com/fido-alliance/how-to-fido/blob/master/HowToFIDO.md  <-- This explains the most common UI flows. very useful
* https://webkit.org/blog/11312/meet-face-id-and-touch-id-for-the-web/
* https://developers.yubico.com/WebAuthn/WebAuthn_Developer_Guide/
* https://developers.yubico.com/WebAuthn/Libraries/Using_a_library.html
* https://www.youtube.com/watch?v=yccBhpdJjJc
* https://developer.mozilla.org/en-US/docs/Web/API/Web_Authentication_API

## Libraries
* https://developers.yubico.com/Software_Projects/WebAuthn-FIDO2/WebAuthn-FIDO2_Server_Libraries/
* https://github.com/duo-labs/webauthn
* https://github.com/duo-labs/py_webauthn

## Code
* https://github.com/wireapp/haskell-fido2

## Also
* https://cheatsheetseries.owasp.org/cheatsheets/Multifactor_Authentication_Cheat_Sheet.html
