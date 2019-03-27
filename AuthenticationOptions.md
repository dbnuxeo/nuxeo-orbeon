# Authentication

## External -> Orbeon

* From Apache: Ensure no privileged headers are present in external request

## Nuxeo <-> Orbeon (Internal)

* From Nuxeo: Header authentication (https://doc.orbeon.com/form-runner/access-control/users#header-driven-method).
* From Orbeon: Pre-shared token authentication for Nuxeo access. (See 1)

### Suggested Changes

1. Add persistence configuration option to include custom header.  Pass token via header.  Headers are serialized as part of HTTP persistence provider. (Ref: https://github.com/orbeon/orbeon-forms/blob/master/form-runner/jvm/src/main/scala/org/orbeon/oxf/fr/persistence/proxy/PersistenceProxyProcessor.scala#L255)
2. Parse the response of a call to the authorization service (https://doc.orbeon.com/xml-platform/controller/authorization-of-pages-and-services#authorization-service) for the JSON body as specified in https://doc.orbeon.com/form-runner/access-control/users#header-driven-method and saved in the session. (Ref: https://github.com/orbeon/orbeon-forms/blob/master/src/main/scala/org/orbeon/oxf/controller/Authorizer.scala#L142)