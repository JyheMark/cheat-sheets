# OpenSSL Cheat Sheet

## Table of Contents

1. [Generating a Private Key](#generating-a-private-key)
2. [Generating a Certificate Signing Request (CSR)](#generating-a-certificate-signing-request-csr)
3. [Generating a Self-Signed Certificate](#generating-a-self-signed-certificate)
4. [Converting a Certificate to Different Formats](#converting-a-certificate-to-different-formats)
    - [PEM to DER](#pem-to-der)
    - [DER to PEM](#der-to-pem)
    - [PEM to PKCS#12 (PFX)](#pem-to-pkcs12-pfx)
5. [Creating a Root Certificate Authority (CA)](#creating-a-root-certificate-authority-ca)
6. [Creating an Intermediate Certificate Authority](#creating-an-intermediate-certificate-authority)
7. [Signing SSL Certificates with an Intermediate CA](#signing-ssl-certificates-with-an-intermediate-ca)
8. [Generating a Certificate Chain](#generating-a-certificate-chain)
9. [Revoking an SSL Certificate](#revoking-an-ssl-certificate)


## Generating a Private Key

To generate a private key, you can use the following command:

```Bash
openssl genrsa -out private.key [key length]
```

For example, to generate a 2048-bit RSA private key, you can use the following command:

```Bash
openssl genrsa -out private.key 2048
```

## Generating a Certificate Signing Request (CSR)

To generate a CSR, you will need to provide some information about your organization and the domain you want to secure. This information will be included in the CSR and will be used to generate the SSL certificate.

To generate a CSR, you can use the following command:

```Bash
openssl req -new -key private.key -out csr.pem
```

This command will prompt you for the necessary information and will generate a CSR file called `csr.pem`.

## Generating a Self-Signed Certificate

To generate a self-signed SSL certificate, you can use the following command:

```Bash
openssl req -x509 -new -key private.key -out certificate.pem -days [validity]
```

For example, to generate a self-signed certificate that is valid for 365 days, you can use the following command:

```Bash
openssl req -x509 -new -key private.key -out certificate.pem -days 365
```

## Converting a Certificate to Different Formats

OpenSSL can be used to convert SSL certificates to and from various formats. Here are some common examples:

### PEM to DER

To convert a PEM-formatted certificate to DER format, you can use the following command:

```Bash
openssl x509 -in certificate.pem -outform der -out certificate.der
```

This command will convert the PEM-formatted certificate in `certificate.pem` to DER format and save it in `certificate.der`.

### DER to PEM

To convert a DER-formatted certificate to PEM format, you can use the following command:

```Bash
openssl x509 -in certificate.der -inform der -out certificate.pem
```

This command will convert the DER-formatted certificate in `certificate.der` to PEM format and save it in `certificate.pem`.

### PEM to PKCS#12 (PFX)

To convert a PEM-formatted certificate and private key to PKCS#12 (PFX) format, you can use the following command:

```Bash
openssl pkcs12 -export -out certificate.pfx -inkey private.key -in certificate.pem
```

This command will prompt you for a password to protect the exported PFX file. You can also specify the password on the command line using the `-passout` option. For example:

```Bash
openssl pkcs12 -export -out certificate.pfx -inkey private.key -in certificate.pem -passout pass:<password>
```

This command will export the certificate and private key in `certificate.pem` and `private.key`, respectively, to a PKCS#12 (PFX) file called `certificate.pfx`.

## Creating a Root Certificate Authority (CA)

To create a root certificate authority (CA), you will first need to generate a private key and a self-signed certificate for the CA. You can use the following steps to do this:

1. Generate a private key for the root CA:

```Bash
openssl genrsa -out root-ca.key [key length]
```

2. Generate a self-signed certificate for the root CA:

```Bash
openssl req -x509 -new -key root-ca.key -out root-ca.pem -days [validity]
```

This will generate a self-signed certificate for the root CA and save it in `root-ca.pem`.

## Creating an Intermediate Certificate Authority

To create an intermediate certificate authority (CA), you will first need to generate a private key and a certificate signing request (CSR) for the intermediate CA. You can then have the root CA sign the intermediate CA's CSR to create a signed certificate for the intermediate CA. You can use the following steps to do this:

1. Generate a private key for the intermediate CA:

```Bash
openssl genrsa -out intermediate-ca.key [key length]
```

2. Generate a CSR for the intermediate CA:

```Bash
openssl req -new -key intermediate-ca.key -out intermediate-ca.csr
```

3. Have the root CA sign the intermediate CA's CSR:

```Bash
openssl x509 -req -in intermediate-ca.csr -CA root-ca.pem -CAkey root-ca.key -CAcreateserial -out intermediate-ca.pem -days [validity]
```

This will generate a signed SSL certificate for the intermediate CA and save it in `intermediate-ca.pem`.

## Signing SSL Certificates with an Intermediate CA

Once you have created an intermediate CA, you can use it to sign SSL certificates for your domain. To do this, you will need to generate a private key and a CSR for the domain, and then have the intermediate CA sign the CSR to create a signed SSL certificate. You can use the following steps to do this:

1. Generate a private key for the domain:

```Bash
openssl genrsa -out domain.key [key length]
```

2. Generate a CSR for the domain:

```Bash
openssl req -new -key domain.key -out domain.csr
```

3. Have the intermediate CA sign the domain's CSR:

```Bash
openssl x509 -req -in domain.csr -CA intermediate-ca.pem -CAkey intermediate-ca.key -CAcreateserial -out domain.pem -days [validity]
```

This will generate a signed SSL certificate for the domain and save it in `domain.pem`.

## Generating a Certificate Chain

When using an intermediate CA to sign SSL certificates, you will need to create a certificate chain that includes the intermediate CA certificate and the root CA certificate. This certificate chain is used to verify the authenticity of the SSL certificate and ensure that it was signed by a trusted CA.

To create a certificate chain, you can concatenate the certificates in the chain into a single file, with the root CA certificate first, followed by the intermediate CA certificate, and finally the server certificate. For example:

```Bash
cat root-ca.pem intermediate-ca.pem server.pem > certificate-chain.pem
```

You can then deploy the `certificate-chain.pem` file to your server and configure it to use the `certificate-chain.pem` file as the SSL certificate and the domain's private key (`domain.key`) as the private key for the SSL connection.

## Revoking an SSL Certificate

If an SSL certificate is compromised or needs to be replaced for any reason, you can revoke it using the root CA or intermediate CA that signed the certificate. To revoke an SSL certificate, you will need to generate a certificate revocation list (CRL) and distribute it to the appropriate parties.

To generate a CRL, you can use the following command:

```Bash
openssl ca -gencrl -out crl.pem -keyfile [private key file] -cert [certificate file]
```

For example, if you want to generate a CRL using the root CA's private key and certificate, you can use the following command:

```Bash
openssl ca -gencrl -out crl.pem -keyfile root-ca.key -cert root-ca.pem
```

This will generate a CRL in `crl.pem` using the root CA's private key and certificate. You can then distribute the CRL to the appropriate parties so that they can check the CRL to determine if an SSL certificate has been revoked.

To revoke an SSL certificate using the CRL, you can use the following command:

```Bash
openssl ca -revoke [certificate file] -keyfile [private key file] -cert [certificate file] -crl_reason [reason]
```

For example, if you want to revoke the `server.pem` certificate using the root CA's private key and certificate, you can use the following command:

```Bash
openssl ca -revoke server.pem -keyfile root-ca.key -cert root-ca.pem -crl_reason keyCompromise
```

This will revoke the `server.pem` certificate using the root CA's private key and certificate. The `-crl_reason` option specifies the reason for revoking the certificate, which will be included in the CRL.

Once you have revoked an SSL certificate, you will need to update the CRL and distribute it to the appropriate parties so that they can check the CRL to determine if an SSL certificate has been revoked. To update the CRL, you can use the following command:

```Bash
openssl ca -gencrl -out crl.pem -keyfile [private key file] -cert [certificate file]
```

For example, if you want to update the CRL using the root CA's private key and certificate, you can use the following command:

```Bash
openssl ca -gencrl -out crl.pem -keyfile root-ca.key -cert root-ca.pem
```

This will regenerate the CRL in `crl.pem` using the root CA's private key and certificate, and include any revoked certificates. You can then distribute the updated CRL to the appropriate parties so that they can check the CRL to determine if an SSL certificate has been revoked.