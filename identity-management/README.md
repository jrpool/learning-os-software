# Identity Management: Authentication, Authorization, and Single-Sign-On (SSO)

## Background

Perhaps the biggest challenge when developing a [service-oriented architecture][soa] is handling authentication (auth) and authorization (authz). In a monolithic app, this challenge is severely reduced: create a users table, a roles table, and a capabilities table, and you're "Good to Go(TM)".

However, in a SOA, we need a way to ensure that every service knows who is making requests, whether they are a valid user, what capabilities (i.e., permissions) they have, etc. Very "public" SOA-providers (e.g., Google, Facebook, GitHub) typically solve this by implementing an [OAuth2][oauth2] provider. At the time of this writing, OAuth2 is the most robust way to provide a way for applications on the platform to authenticate and authorize various operations. However, there's a pretty large up-front cost to building out an OAuth2 provider.

We have _not_ at this time implemented an OAuth2 provider.

## A Simpler Alternative: JSON Web Tokens (JWT)

Enter JSON Web Tokens (JWT).

JWTs are an open, industry-standard ([RFC7519][rfc7519]) method for representing claims securely between two parties.

### How JWTs Work At Learners Guild

We have a centralized [Identity Management (IDM)][idm] service. It is responsible for keeping track of all of the users in the system. It's also responsible for providing SSO functionality. _Besides having a basic understanding of how JWTs work_, all you need to know about the implementation of JWTs within the IDM service is that, when _signing_ the JWT, IDM uses the _private_ key from a private / public keypair. Any service that wishes to _verify_ the token uses the _public_ key.

#### The JWT Cookie

Upon successful authentication, and, in fact, during each request-response cycle, the IDM service will create or update a special cookie, named **`lgJWT`**, the value of which is the signed JWT. As a best-practice, this cookie is an HTTP-only, secure cookie, but any service within the `learnersguild.org` domain should be able to read it.

#### The JWT Contents

All JWTs contain a series of "claims". Two claims, in particular, are important when verifying a JWT: `iss` (issuer, in our case, `learnersguild.org`) and `exp` (expiration date). If you are implementing a service and want to validate a JWT provided in a request header (or the aforementioned cookie), you'll need to ensure that:

1. The `iss` claim == `learnersguild.org`.
2. The `exp` claim is a [Unix timestamp][unix-time] in the future.

If both of those things are true, you can get the rest of the user information from the JWT using (mostly) standard claims, plus a few extras:

##### Standard Claims

```
iss: (issuer)
iat: (issued at timestamp)
exp: (token expiry timestamp)
sub: (user UUID)
name: (user name)
preferred_username: (user handle)
email: (user primary email)
birthdate: (user date of birth)
zoneinfo: (user timezone)
phone_number: (user phone number)
```

##### Additional Claims

```
emails: (all user email addresses)
roles: (user roles)
```

### Limitations of JWT

When compared to OAuth2, JWTs have one main limitation. In OAuth2, it's possible for the OAuth2 provider to disable individual applications and services by invalidating any tokens associated with those services. JWTs don't support this. The good news, however, is that JWTs can use public-key cryptography to get 80% of the way there. In practice, this means that, when using JWTs, if the provider wants to disable a particular service or application, a new private / public keypair needs to be generated. Then, the new _public_ key can be shared with any services that should continue to be enabled. While this would be incredibly inconvenient for an ecosystem with hundreds or thousands of applications, it is perfectly sufficient for early Learners Guild development. Furthermore, there's nothing to stop us from implementing an OAuth2 provider in the future, and in fact, we may do so.

### Example implementation

The [idm-jwt-auth][idm-jwt-auth] npm module can be used for services built using Node.js to handle all of the behind-the-scenes stuff necessary for SSO via IDM. For services built on other frameworks and platforms, it should provide a reasonable reference for how to work with the tokens.



[soa]: ../global-requirements/soa.md
[oauth2]: http://oauth.net/2/
[jwt]: http://jwt.io/
[rfc7519]: https://tools.ietf.org/html/rfc7519
[idm]: https://idm.learnersguild.org
[unix-time]: https://en.wikipedia.org/wiki/Unix_time
[idm-jwt-auth]: https://github.com/LearnersGuild/idm-jwt-auth
