# flogo-crypto-func

This is a test application for flogo extension cryptographic function library.


## Cryptographic function library

The function extension library is available here https://github.com/mmussett/flogo-extensions


## AES Encryption and Decryption


* crypto.aesEncrypt(plaintext, key)
* crypto.aesDecrypt(ciphertext, key)

Example:

### AES Encryption using shared secret
```
crypto.aesEncrypt($flow.body.msg, $property["AESKEY"])
```


### AES Decryption using shared secret
```
crypto.aesEncrypt($flow.body.msg, $property["AESKEY"])
```


## RSA Encryption and Decryption

* crypto.rsaEncrypt(plaintext,rsaPublicKey)
* crypto.rsaDecrypt(ciphertext,rsaPrivateKey)


Due to limitation in how PEM formatted keys are stored in Flogo properties you must encode the PEM certificate using Base64 prior to setting the flogo property. Failure to encode the PEM certificate will cause an error at runtime. When setting the rsaPublicKey parameter you must decode the PEM certificate string using utils.decodeBase64($property[]). 

Example:

### Encrypting using public key 
```
crypto.rsaEncrypt($flow.body.msg,coerce.toString(utils.decodeBase64($property["RSAPUBKEY"])))

```

### Decrypting using private key
```
crypto.rsaDecrypt($flow.body.msg, coerce.toString(utils.decodeBase64($property["RSAPRIVKEY"])))
```