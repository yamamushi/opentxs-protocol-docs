# OTServerContract Summary

This class derives from [OTContract](OTContract.md) and provides methods for
creating an loading authenticated server references.

# Purpose

The contract allows for secure communication with a remote server. The server
data (hostname and port) is signed by the contract's _signer_ Nym and the
corresponding credentials.

These credentials can be used to

* Encrypt outgoing messages to the server using `OTEnvelope::Seal` and
  `OTEnvelope::Encrypt()`
* Verify incoming messages by checking the server signature using
  `OTContract::VerifySignature()`

TODO: details figure out *where* this actually happens

# Structure

The XML of this contract extends the superclass using the classical method:

* Override `CreateContents()` to write custom XML elements
* Override `ProcessXMLNode()` to read custom XML elements

```xml
<?xml version="1.0">
<notaryProviderContract version="2.0">
    <entity shortname="$shortname"
            longname="$longname"
            serverURL="$serverURL">

    <notaryServer hostname="$hostname"
                  port="$port"
                  URL="$url" />

    <!-- CreateInnerContents() -->
</notaryProviderContract>
```