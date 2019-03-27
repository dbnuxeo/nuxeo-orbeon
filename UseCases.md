# Orbeon Use Cases

## New Request for Customer

```sequence
Title: New Customer Form
User->Nuxeo: Create Form Request
Nuxeo->Nuxeo: Generate access token
Nuxeo->Orbeon: Create Form
Nuxeo->>Customer: Send email notification w/token
```

## Customer Accesses Form

```sequence
Title: Customer Input
Customer->Nuxeo: Load Form URL
Nuxeo-->Customer: Token Authentication Form
Customer->Nuxeo: Submit Token
Nuxeo-->Customer: Redirect to Orbeon
Customer->Orbeon: Get Form
Orbeon->Nuxeo: Get Customer Information
Nuxeo-->Orbeon: Provide Customer Accesses
Orbeon-->Customer: Display Form
Customer->Orbeon: Submit Form
Orbeon->Nuxeo: Save Form Data
Nuxeo->>User: Send Form Completed Notification
Orbeon-->Customer: Display Saved Form
```

## User Verifies Form

```sequence
Title: User Verifies Form
User->Nuxeo: Validate Form Data
Nuxeo->Orbeon: Revoke Customer Edit Permission
Note left of Orbeon: Customer will have view access
Nuxeo-->User: Complete Verification
```