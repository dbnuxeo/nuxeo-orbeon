# Orbeon Use Cases

## New Request for Customer

```sequence
Title: New Customer Form
User->Nuxeo: Create Form Request
Nuxeo->Nuxeo: Generate access token
Nuxeo->Orbeon: Provision Form
Nuxeo->>Customer: Send email notification
```

## Customer Accesses Form

```sequence
Title: Customer Input
Customer->Nuxeo: Load Form URL
Nuxeo-->Customer: Token Authentication
Customer->Nuxeo: Submit Token
Nuxeo-->Customer: Redirect to Orbeon
Customer->Orbeon: Get Form
Orbeon->Nuxeo: Get Customer Information
Nuxeo-->Orbeon: Provide Customer Accesses
Orbeon-->Customer: Display Form

```