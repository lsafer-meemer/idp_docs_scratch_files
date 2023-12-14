### Redirection

Redirect Uri `redirect_uri`
: REQUIRED. Redirection URI to which the response will be sent.

Response Mode `response_mode`
: OPTIONAL. Informs the Authorization Server of the mechanism to be used for returning Authorization Response
parameters from the Authorization Endpoint.

State `state`
: RECOMMENDED. An opaque value used by the `client` to maintain
state between the request and callback.

### Authentication

Prompt Set `prompt`
: OPTIONAL. Space delimited, case-sensitive list of ASCII string values that specifies whether the
Authorization Server prompts the End-User for reauthentication and consent.

Max Age `max_age`
: OPTIONAL. Maximum Authentication Age. Specifies the allowable elapsed time in seconds since the last time the
End-User was actively authenticated by the OP.
If the elapsed time is greater than this value, the OP MUST attempt to actively re-authenticate the End-User.
(The max_age request parameter corresponds to the OpenID 2.0 PAPE max_auth_age request parameter.)
When max_age is used, the ID Token returned MUST include an auth_time Claim Value.

ACR Values `acr_values` or `claims.identity.acr.values`
: OPTIONAL. Requested Authentication Context Class Reference values. Space-separated string that specifies the
acr values that the Authorization Server is being requested to use for processing this Authentication Request,
with the values appearing in order of preference.
The Authentication Context Class satisfied by the authentication performed is returned as the acr Claim Value,
as specified in Section 2. The acr Claim is requested as a Voluntary Claim by this parameter.

ACR Essential `claims.identity.acr.essential`
: causes the authorization request to fail when ACR cannot be met

AMR Values `claims.identity.amr.values`
: OPTIONAL. Authentication Methods References.
JSON array of strings that are identifiers for authentication methods used in the authentication.
For instance, values might indicate that both password and OTP authentication methods were used.
The definition of particular values to be used in the amr Claim is beyond the scope of this specification.
Parties using this claim will need to agree upon the meanings of the values used, which may be context-specific.
The amr value is an array of case-sensitive strings.

Subject `id_token_hint.sub` or `claims.identity.sub`
: If present, the authorization server should attempt to complete the authorization for an account
with an id identical to this value.

### Returns

Scope Set `scope`
: REQUIRED. The scope of the access request

Identity Standard Claims `claims.identity`
: standard claims requested using the claims parameter to be returned in the identity token

Userinfo Standard Claims `claims.userinfo`
: standard claims requested using the claims parameter to be returned from the userinfo endpoint

Claims Locales `claims_locales`
: OPTIONAL. End-User's preferred languages and scripts for Claims being returned, represented as a
space-separated list of BCP47 `RFC5646` language tag values, ordered by preference.

Nonce `nonce`
: OPTIONAL. String value used to associate a Client session with an ID Token

### Code Challenge

Code Challenge `code_challenge`
: REQUIRED. Code challenge.

Code Challenge Method `code_challenge_method`
: OPTIONAL, defaults to "plain" if not present in the request.
Code verifier transformation method is "S256" or "plain".

### Experience

Login Hint `login_hint`
: OPTIONAL. Hint to the Authorization Server about the login identifier the End-User might use to log in (if
necessary). This hint can be used by an RP if it first asks the End-User for their e-mail address (or other
identifier) and then wants to pass that value as a hint to the discovered authorization service.
It is RECOMMENDED that the hint value match the value used for discovery.
This value MAY also be a phone number in the format specified for the phone_number Claim.
The use of this parameter is left to the OP's discretion.

UI Locales `ui_locales`
: OPTIONAL. End-User's preferred languages and scripts for the user interface, represented as a space-separated
list of BCP47 `RFC5646` language tag values, ordered by preference.

Display `display`
: OPTIONAL. ASCII string value that specifies how the Authorization Server displays the authentication and
consent user interface pages to the End-User.
