# Build Your Own Certificate Authority (CA)

A Certificate Authority (CA) is the core component of a public key infrastructure (PKI) responsible for establishing a hierarchical chain of trust. CAs issue the digital credentials used to certify the identity of users. 

According to wiki, certification authority (CA) is an entity that issues digital certificates. A digital certificate certifies the ownership of a public key by the named subject of the certificate. This allows others (relying parties) to rely upon signatures or on assertions made about the private key that corresponds to the certified public key. A CA acts as a trusted third party—trusted both by the subject (owner) of the certificate and by the party relying upon the certificate. The format of these certificates is specified by the X.509 standard.  

In order to mitigate attacks against Certificate Authorities, a Hardware Security Module is require to ensure and maintain the integrity of a PKI.

## Background

It's not many times you get a chance to work on something interesting, when a company decided to build their own public key infrastructure (PKI) and entrusted you with a job. 

The core component was to start with internal CA to generate asymmetric keys to provide secure communication between our internal and hybrid infrastructure with our clients. However, In order to build PKI you need more than CA, you need a root certificate, multiple Intermediate Certificates and policy certificates. As a whole you need to start building your own certificate chain. 


## Certificate Chain

When you decide to create a CA, the decision comes down to building a certificate chain, a two, three or four tier certificate chain.  Below are the examples for certificate chain and validity of certificates.I will leave this with you to decide what level of security and complexity you want to achieve in this job.

### Two tier certificate chain
+---------------+		    +---------------+		    +---------------+
|  Root CA   	|			| Intermediate  |			|  End-User    	|
|   25 Yrs   	|-----------|   CA  10 Yrs	|-----------|  Certificate  |
|            	|			|          		|           |	1 Yr		|
+---------------+           +---------------+           +---------------+

### Three tier certificate chain
+---------------+		    +---------------+		    +---------------+			+---------------+		    
|  Root CA   	|			| Intermediate  |			|  Policy CA   	|			|  End-User		|
|   25 Yrs   	|-----------|   CA  10 Yrs	|-----------|	5 Yrs   	|-----------|  Certificate  |
|            	|			|          		|           |				|           |	1 Yr		|
+---------------+           +---------------+           +---------------+           +---------------+  

### Four tier certificate chain
+---------------+		    +---------------+		    +---------------+			+---------------+			+---------------+		    
|  Root CA   	|			| Intermediate  |			|  Policy CA   	|			|  End-User CA  |			|  End-User		|
|   25 Yrs   	|-----------|   CA  10 Yrs	|-----------|	5 Yrs   	|-----------|	3 Yrs   	|-----------|  Certificate  |
|            	|			|          		|           |				|           |				|			|	1 Yr		|
+---------------+           +---------------+           +---------------+           +---------------+      		+---------------+ 


## Generate root keys 

In order to generate a root key you need to buy your own Hardware Security Module or use cloud vendors HSM.

Buy HSM
https://shop.nitrokey.com/shop/product/nitrokey-hsm-2-7
https://www.yubico.com/product/yubihsm-2/

Cloud HSM 
AWS - https://aws.amazon.com/cloudhsm/
Google - https://cloud.google.com/hsm/
Azure - https://docs.microsoft.com/en-us/azure/dedicated-hsm/

Once you have HSM; You have to generate a root key.

## Generate root CA 



## Resource

https://en.wikipedia.org/wiki/Certificate_authority
https://en.wikipedia.org/wiki/X.509#Certificate_chains_and_cross-certification
https://security.stackexchange.com/questions/189339/why-is-an-hsm-required-to-protect-ca-certificates-rather-than-a-regular-usb-tok
https://www.yubico.com/product/yubihsm-2/
https://shop.nitrokey.com/shop/product/nitrokey-hsm-2-7
https://knowledge.digicert.com/solution/SO7555.html
https://en.wikipedia.org/wiki/PKCS_11

## Discussion

This will provide you an overview to understand and build your own certificate chain.

Have you implemented this solution?

Yes, I implemented this solution and successfully built a four tier certificate chain.
