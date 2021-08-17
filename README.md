# Self Signed SSL

This script simplifies the creation of certificate authorities, signing requests and self-signed TLS certificates using OpenSSL.

[Video Tutorial](https://www.youtube.com/watch?v=uiQW5QBnGRo)

[![Self-Signed SSL - Introduction Video](./.etc/thumbnail.gif)](https://www.youtube.com/watch?v=uiQW5QBnGRo)

<br />

## Installation

<br />

**Homebrew (MacOS)**

```
brew tap lstellway/formulae
brew install lstellway/formulae/self-signed-ssl
```

<br />

**cURL**

```
curl --output self-signed-ssl https://raw.githubusercontent.com/lstellway/self-signed-ssl/master/self-signed-ssl && chmod +x self-signed-ssl
```

<br />

## Usage

```shell
self-signed-ssl [OPTIONS]

# Run with no arguments to be prompted for required values
self-signed-ssl

# Only create a certificate authority and trust the generated certificate
self-signed-ssl --ca-only --trust

# Only create a certificate signing request
self-signed-ssl --csr-only

# Generate a signed certificate using existing files
self-signed-ssl --ca='/path/to/CA.pem' --ca-key='/path/to/CA.key' --csr='/path/to/EXAMPLE.csr'

# Automate certificate generation
self-signed-ssl --no-interaction -c 'US' -s 'California' -l 'Los Angeles' -o 'Example Org' -u 'Example Unit' -n 'example.com' -a 'www.example.com'
```

<br />

## Options

<br />

**General**

| Option                        | Description                                                                                           |
| ----------------------------- | ----------------------------------------------------------------------------------------------------- |
| `-h` `--help`                 | Display help and exit                                                                                 |
| `-v` `--version`              | Display the script version and exit                                                                   |
| `-p VALUE` `--path=VALUE`     | Path to output generated keys                                                                         |
| `-d VALUE` `--duration=VALUE` | Number of days the certificate is valid (default `365`)                                               |
| `-b VALUE` `--bits=VALUE`     | Key size in bits (default `2048`)                                                                     |
| `--no-interaction`            | Disables interactive prompts for unspecified variables. <br />_(OpenSSL may still prompt for values)_ |

<br />

**Certificate Authority**

| Option           | Description                                                                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `--ca=VALUE`     | Path to certificate authority cert file <br />_(Generates new CA if not set)_                                                             |
| `--ca-key=VALUE` | Path to certificate authority key file <br/>_(Generates new CA if not set)_                                                               |
| `--ca-only`      | Instructs script to solely generate a certificate authority                                                                               |
| `--ca-ext`       | Allow passing extensions to the CA request                                                                                                |
| `-t` `--trust`   | Flag to trust certificate authority _(requires `sudo` privileges)_<br />_(Currently supports Darwin/MacOS, Fedora/CentOS, Debian/Ubuntu)_ |

<br />

**Certificate Signing Request**

| Option       | Description                                                                                        |
| ------------ | -------------------------------------------------------------------------------------------------- |
| `--csr`      | Path to certificate signing request <br />_(Generates new certificate signing request if not set)_ |
| `--csr-only` | Instructs script to solely generate a certificate signing request                                  |

<br />

**Certificate / Subject**

| Option                            | Description                                                                                          |
| --------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `--extfile=VALUE`                 | Path to file containing OpenSSL certificate extensions<br />_(Optional - generated if not provided)_ |
| `-c VALUE` `--country=VALUE`      | Country Name (2 letter code)                                                                         |
| `-s VALUE` `--state=VALUE`        | State or Province Name (full name)                                                                   |
| `-l VALUE` `--locality=VALUE`     | Locality Name (eg, city)                                                                             |
| `-o VALUE` `--organization=VALUE` | Organization Name (eg, company)                                                                      |
| `-u VALUE` `--unit=VALUE`         | Organizational Unit Name (eg, section)                                                               |
| `-n VALUE` `--common-name=VALUE`  | Common Name (e.g. server FQDN or YOUR name)                                                          |
| `-a VALUE` `--san=VALUE`          | Comma-delimited list of subject alternative names _(Subdomains, etc..)_                              |
| `-e VALUE` `--email=VALUE`        | Email Address                                                                                        |

<br />

## Resources

-   [OpenSSL 1.1.1 Manual](https://www.openssl.org/docs/man1.1.1/man1/)
-   [Issues / Feature Requests](https://github.com/lstellway/self-signed-ssl/issues)
