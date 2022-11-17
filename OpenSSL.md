# OpenSSL CLI tool cheat sheet

## Generate CA

Create RSA key
```bash
openssl genrsa -aes256 -out ca-key.pem
```

Generate public CA cert
```bash
openssl req -new -x509 -sha256 -days 365 -key ca-key.pem -out ca.pem
```

### Generate Certificate
Create RSA key
```bash
openssl genrsa -out cert-key.pem
```

Create a Certificate Signing Request (CSR)
```bash
openssl req -new -sha256 -subj "/CN=yourcn" -key cert-key.pem -out cert.csr
```

Create an *extfile* with alternative names

```bash
echo "subjectAltName=DNS:your-dns.record,IP:123.123.123.123" >> extfile.cnf
# optional
echo "extendedKeyUsage = serverAuth >> extfile.cdn"
```

Create the certificate
```bash
openssl x509 -req -sha256 -days 365 -in cert.csr -CA ca.pem -CAkey ca-key.pem -out cert.pem -extfile extfile.cnd -CAcreateserial
```

## Certificate Formats

X.509 Certificates
- Base64 Formats PEM (.pem, .crt, .ca-bundle)
- PKCS#7 (.p7b, p7s)
- Binary Formats DER (.der, .cer)
- PKCS#12 (.pfx, p12).

| Command                                                               | Conversion |
|-----------------------------------------------------------------------|------------|
|openssl x509 -outform der -in cert.pem -out cert.der                   | PEM to DER |
|openssl x509 -inform der -in cert.der -out cert.pem                    | DER to PEM |
|openssl pkcs12 -in cert.pfx -out cert.pem -nodes                       | PFX to PEM |
|openssl pkcs12 -inkey cert-key.pem -in cert.pem -export -out -cert.pfx | PEM to PFX |

## Verify Certificates
```bash
openssl verify -CAfile ca.pem -verbose cert.pem
```