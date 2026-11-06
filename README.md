# NIP-86 · Relay Management API on LiberNet

> Relay Management API, as used by the **LiberNet** apps.

**Official spec:** [nostr-protocol/nips · 86.md](https://github.com/nostr-protocol/nips/blob/master/86.md)
**Status upstream:** `draft` `optional`
**Maintainer of this repo:** Luciano "Barak" Casalunga ([@lucianocasalunga](https://github.com/lucianocasalunga)) · [libernet.app](https://libernet.app)

## My role

I took part in the creation of NIP-86, and it runs across the LiberNet apps.

## Why NIP-86 matters for LiberNet

Running a community relay means moderating it. NIP-86 is a JSON-RPC API over HTTP on the relay's own URL, so LiberNet can ban, allow and manage pubkeys and events with standard tools. It also provides `createclaim`, the invite codes used by [NIP-43](https://github.com/lucianocasalunga/nip-43).

## How it works (quick reference)

Request: `Content-Type: application/nostr+json+rpc`, authorized with a NIP-98 event.

| Method | Purpose |
|--------|---------|
| `supportedmethods` | List available methods |
| `banpubkey` / `unbanpubkey` | Ban or unban a pubkey |
| `allowpubkey` / `unallowpubkey` | Manage the allow list |
| `listbannedpubkeys` / `listallowedpubkeys` | List them |
| `banevent` / `allowevent` | Moderate single events |
| `changerelayname` / `changerelaydescription` | Edit relay info |

### Example: banning a spammer

```http
POST / HTTP/1.1
Host: relay.libernet.app
Content-Type: application/nostr+json+rpc
Authorization: Nostr <base64 NIP-98 event>

{"method": "banpubkey", "params": ["<hex pubkey>", "spam"]}
```

## Related LiberNet NIPs

[NIP-43](https://github.com/lucianocasalunga/nip-43) · [NIP-45](https://github.com/lucianocasalunga/nip-45) · [NIP-50](https://github.com/lucianocasalunga/nip-50) · [NIP-66](https://github.com/lucianocasalunga/nip-66) · [NIP-67](https://github.com/lucianocasalunga/nip-67) · [NIP-70](https://github.com/lucianocasalunga/nip-70) · [NIP-77](https://github.com/lucianocasalunga/nip-77) · [NIP-95 (my proposal)](https://github.com/lucianocasalunga/nip-95)

---
Nostr since 2021 · Part of the LiberNet ecosystem
