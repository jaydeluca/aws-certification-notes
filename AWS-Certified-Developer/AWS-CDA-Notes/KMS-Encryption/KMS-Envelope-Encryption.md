# KMS Envelope Encryption
Envelope Encryption is simply the process of encrypting your Envelope Key

Your Envelope key is essentially the key you use to decrypt your data. AWS KMS system takes a Master Key and use it to Encrypt our Envelope Key, and the Evenlope Key is used to encrypt our data

## Encryption with AWS

![Image](https://i.imgur.com/5btpZI3.jpg)

## Decryption with AWS

![Image](https://i.imgur.com/q5Fyw1z.jpg)

## AWS Envelope Encryption - Exam Tips
**The Customer Master Key:**

   - Customer Master Key used to decrypt the data key (envelope key)
   - Envelope Key is used to decrypt the data
    
- The Customer Master Key is used to encrypt and decrypt the Envelope Key or Data Key
- The Envelope Key or Data Key is used to encrypt and decrypt plain text files

Exam Question:

**How is the AWS Encryption SDK different from the Amazon S3 encryption client?**

The Amazon S3 encryption client in the AWS SDK for Java, AWS SDK for Ruby, and AWS SDK for .NET provides encryption and decryption for data that you store in Amazon Simple Storage Service (Amazon S3). These clients are tightly coupled to Amazon S3 and are intended for use only with data stored there.

The AWS Encryption SDK provides encryption and decryption for data that you can store anywhere. The AWS Encryption SDK and the Amazon S3 encryption client are not compatible because they produce ciphertexts with different data formats.

