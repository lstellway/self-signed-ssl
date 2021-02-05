# Self Signed TLS

This is script to simplify the creatiion of a certificate authority and self-signed TLS certificates using OpenSSL.

<br />

## Usage

```
self-signed-tls [OPTIONS]
self-signed-tls --trust -c US -s California -l 'Los Angeles' -o 'Example Org' -u 'Example Unit'
self-signed-tls --ca-key=/path/to/CA.key --ca-cert=/path/to/CA.pem
```

<br />

## Options

**General**

-   **-h|--help**
    -   Display help and exit
-   **-p|--path**
    -   Path to output generated keys
-   **-d|--duration**
    -   Validity duration of the certificate (in days)
-   **-b|--bits**
    -   Key size in bits (default `2048`)

<br />

**Certificate Authority**

-   **--ca-key**
    -   Path to certificate authority key file <br/>_(Generates new CA if not set)_
-   **--ca-cert**
    -   Path to certificate authority cert file <br />_(Generates new CA if not set)_
-   **-t|--trust**
    -   Flag to trust certificate authority _(requires `sudo` privileges)_<br />_(Do not set for default 'false')_<br />_(Currently only supports Darwin / MacOS. Please feel free to contribute if you know how to trust a certificate on other systems.)_

<br />

**Certificate Subject**

-   **-c|--country**
    -   Country Name (2 letter code)
-   **-s|--state**
    -   State or Province Name (full name)
-   **-l|--locality**
    -   Locality Name (eg, city)
-   **-o|--organization**
    -   Organization Name (eg, company)
-   **-u|--unit**
    -   Organizational Unit Name (eg, section)
-   **-n|--common-name**
    -   Common Name (e.g. server FQDN or YOUR name)
-   **-a|--san**
    -   Comma-delimited list of subject alternative names
-   **-e|--email**
    -   Email Address
