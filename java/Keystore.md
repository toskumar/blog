# Keystore 

A keystore is a repository where private keys, certificates and symmetric keys can be stored. [KeyStore Explorer](https://keystore-explorer.org/) is an open source GUI replacement for the Java command-line utilities keytool and jarsigner.


## How to create a self-signed certificate using java keytool

```
keytool -genkeypair -keystore mykeystore.jks -storetype pkcs12 -dname "CN=localhost, OU=Unknown, 
  O=Unknown, L=Unknown, ST=Unknown, C=Unknown" -keypass password123 -storepass password123 
  -keyalg RSA -sigalg SHA1withRSA -keysize 2048 -alias mykeyAlias 
  -ext SAN=DNS:localhost,IP:127.0.0.1 -validity 365
```
## How to create a seceret key 

```
keytool -genseckey -alias aes128key -keyalg AES -keysize 128 -keystore mykeystore.jks 
-storepass password123 -storetype pkcs12
```

## How to list the entries in the keystore file

```
keytool -list -v -storepass password123 -keystore mykeystore.jks
```

## How to delete an entry in the keystore file

```
keytool -delete -alias mykeyAlias -keystore mykeystore.jks -storetype pkcs12 -keypass password123 
-storepass password123
```
