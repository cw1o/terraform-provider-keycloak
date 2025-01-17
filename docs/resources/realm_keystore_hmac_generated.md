---
page_title: "keycloak_realm_keystore_hmac_generated Resources"
---

# keycloak\_realm\_keystore\_hmac_generated Resources

Allows for creating and managing `hmac-generated` Realm keystores within Keycloak.

A realm keystore manages generated key pairs that are used by Keycloak to perform cryptographic signatures and encryption.

## Example Usage

```hcl
resource "keycloak_realm" "realm" {
	realm = "my-realm"
}

resource "keycloak_realm_keystore_hmac_generated" "keystore_hmac_generated" {
	name      = "my-hmac-generated-key"
	realm_id  = keycloak_realm.realm.realm

	enabled = true
	active  = true

	priority     = 100
	algorithm    = "HS256"
	secret_size  = 64
}
```

## Argument Reference

- `name` - (Required) Display name of provider when linked in admin console.
- `realm_id` - (Required) The realm this keystore exists in.
- `enabled` - (Optional) When `false`, key is not accessible in this realm. Defaults to `true`.
- `active` - (Optional) When `false`, key in not used for signing. Defaults to `true`.
- `priority` - (Optional) Priority for the provider. Defaults to `0`
- `algorithm` - (Optional) Intended algorithm for the key. Defaults to `HS256`
- `secret_size` - (Optional) Size in bytes for the generated secret. Defaults to `64`.

## Import

Realm keys can be imported using realm name and keystore id, you can find it in web UI.

Example:

```bash
$ terraform import keycloak_realm_keystore_hmac_generated.keystore_hmac_generated my-realm/my-realm/618cfba7-49aa-4c09-9a19-2f699b576f0b
```
