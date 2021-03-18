# Self Signed TLS

This is script to simplify the creation of certificate authorities and self-signed TLS certificates using OpenSSL.

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

| Option | Description |
| ------ | ----------- |
| `-h` `--help` | Display help and exit |
| `-p VALUE` `--path=VALUE` | Path to output generated keys |
| `-d VALUE` `--duration=VALUE` | Validity duration of the certificate (in days) |
| `-b VALUE` `--bits=VALUE` | Key size in bits (default `2048`) |

<br />

**Certificate Authority**

| Option | Description |
| ------ | ----------- |
| `--ca-key=VALUE` | Path to certificate authority key file <br/>_(Generates new CA if not set)_ |
| `--ca-cert=VALUE` | Path to certificate authority cert file <br />_(Generates new CA if not set)_ |
| `-t` `--trust` | Flag to trust certificate authority _(requires `sudo` privileges)_<br />_(Do not set for default 'false')_<br />_(Currently only supports Darwin / MacOS. Please feel free to contribute if you know how to trust a certificate on other systems.)_ |

<br />

**Certificate Subject**

| Option | Description |
| ------ | ----------- |
| `-c VALUE` `--country=VALUE` | Country Name (2 letter code) |
| `-s VALUE` `--state=VALUE` | State or Province Name (full name) |
| `-l VALUE` `--locality=VALUE` | Locality Name (eg, city) |
| `-o VALUE` `--organization=VALUE` | Organization Name (eg, company) |
| `-u VALUE` `--unit=VALUE` | Organizational Unit Name (eg, section) |
| `-n VALUE` `--common-name=VALUE` | Common Name (e.g. server FQDN or YOUR name) |
| `-a VALUE` `--san=VALUE` | Comma-delimited list of subject alternative names |
| `-e VALUE` `--email=VALUE` | Email Address |
