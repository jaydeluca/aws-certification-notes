# KMS API Calls

```sh
aws kms encrypt --key-id YOURKEYIDHERE --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt
aws kms re-encrypt --destination-key-id YOURKEYIDHERE --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt 
aws kms enable-key-rotation --key-id YOURKEYIDHERE
```

## KMS API Calls -Exam Tips
- aws kms encrypt
- aws kms decrypt
- aws kms re-encrypt (take your encrypted one and instead of decrypt it into plaintext, it will re-encrypt and destroy the plaintext one)
- aws kms enable-key-rotation
