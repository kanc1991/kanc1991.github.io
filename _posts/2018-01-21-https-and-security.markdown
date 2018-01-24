---
layout: post
title:  "Https and Network Security"
date:   2018-01-21
---
## The problem

Internet has made people's life much more convenient than ever before. However, people's credentials as
well as their personal information are at the risk of being stolen through web attackers.

For Example:
- While you are attempting to login to facebook, how do you know you are giving your password to the "real"
facebook instead of a hacker's website. Their website can look exactly the same as facebook.com.
- While you are making a purchase through Amazon.com, how do you make sure your credit card info is only
visible to Amazon? Even If it's indeed Amazon.com, how do you make sure those info are not intercepted by
some one in the middle?

![hacker](/assets/hacker.jpg)

That's why today we are mostly using https instead of http.

##  What's https and how it works
Https is a secure version of HTTP built over TLS. Essentially all information exchanged between client and
server are symmetrically encrypted with something called session key. The session key was securely exchanged
during TLS handshake. Following is a rough summary of how TLS handshake works.

![TLS_handshake](/assets/TLS_handshake.jpg)

More details can be find online. I'll list a few items here:
- There's also mutual TLS application where certificate of client is also required
- During handshake actually pre-master secret is exchanged. Both server and client
can generate session key based on that.
- handshake not only exchanges the session key(pre-master secret), but also authenticates
the server. That will be covered.

##  How does the client verify server's identity based on server's certificate
We call this chain of trust.

![chain_of_trust](/assets/chain_of_trust.png)

Say I'm running a business site https://www.flower.com, in order to allow client's browser to verify my identity, I'll need to have my certificate signed by some CA (certificate authority). Say I found google as an intermediate CA who signed my cert with their private key. Similarly google's cert also signed by a root CA's private key, let's say root CA is some trusted company called geoTrust.

Typically, browsers are pre-installed with root CA's public keys. Therefore, once my https://www.flower.com send a server hello message to the browser along with both google's and my certificates. First browser will validate google's cert using geoTrust's public key which is pre-installed. Then it'll validate my site's certificate with google's public key (contained in google's cert). In summary, the browser trust CA's. CA trust goole and google trust my site. Thus browser would trust my site and thus establish an https session with my site.

For root CA's. They can be self signed as they don't need other authority to provide signature to them.
