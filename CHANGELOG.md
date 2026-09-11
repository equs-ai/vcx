# Changelog

All notable changes to this fork are documented here.

This is a fork of [openwallet-foundation/vcx](https://github.com/openwallet-foundation/vcx)
(formerly `hyperledger/aries-vcx`), diverged at `82a481d`.

### Changed

- **Breaking:** DID document service endpoints accept the DIDComm v2 object form
  and lists, not just a URL. `Service`, `ServiceDidCommV1`, `ServiceDidCommV2`
  and `did_peer`'s numalgo-2 / numalgo-4 encoding are typed `OneOrList<Endpoint>`;
  callers wrap a URL as `OneOrList::One(Endpoint::Uri(url))` and read it back
  through `TryInto<Url>`.
- Only `did_doc` and `did_peer` were updated; `did_resolver_sov`, `did_cheqd` and
  `aries_vcx` still pass a `Url` and do not build against the new type.
- A `serviceEndpoint` that is not a valid URL is no longer rejected when parsing
  a DID document; it now fails later, on conversion to a `Url`.
- `chrono`'s `alloc` feature enabled in `did_resolver`.
