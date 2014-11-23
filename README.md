## What ##
A simple, naive modification of release Apple's mDNSResponder release
561.1.1:

[http://opensource.apple.com/source/mDNSResponder/mDNSResponder-561.1.1/](http://opensource.apple.com/source/mDNSResponder/mDNSResponder-561.1.1/)

to support registration of A records without a corresponding
PTR record. Changes in OSX10.10 Yosemite, present in 10.10.1 do not
allow resolution of CNAME records. We cannot simply add more A records
because mdnsd will reject a registration request for a duplicate PTR:

`DNSCoreReceiveResponse: Unexpected conflict discarding`

so we permit the creation of A records without a corresponding PTR
record, using the Proxy Responder.

## Why ##
.local name resolution for local virtual machine-based development.

