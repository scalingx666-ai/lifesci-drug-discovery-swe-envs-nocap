# Issue

**Title:** feat: JWT-based authentication for Hub API requests

## Description

# Description

This PR implements a JWT-based authentication system when making request to the Polaris Hub API.

It does this by leveraging the OAuth Token Exchange flow ([RFC8693](https://datatracker.ietf.org/doc/html/rfc8693)) in order to exchange the non-JWT token provided by the external authentication service and obtaining a Hub-issued JSON Web Token. That JWT is then used in the authentication header for requests made to the Hub API.

I've split the responsabilities between two authlib clients:

- An external auth client: This client mediates the authentication, and the token fetch/refresh with the external authentication service. (Currently Clerk.)
- A Hub client: This client mediates the exchange of tokens, and ensures Hub API calls are using the JWt for authentication.

Along the way, I've refactored out the token file caching mechanism into subclasses of authlib's `TokenAuth` class, to lighten the client code, and make it easier to test. 

# Links
-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `140d01a16674`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.