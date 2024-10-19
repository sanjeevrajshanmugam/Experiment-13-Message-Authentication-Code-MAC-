# Experiment 13: Message Authentication Code (MAC)

## AIM:
To implement a Message Authentication Code (MAC) using a cryptographic hash function to ensure the integrity and authenticity of a message.



## DESIGN STEPS:

### Step 1:
Design the algorithm to generate and verify the Message Authentication Code (MAC).

### Step 2:
Implement the MAC using a suitable programming language (C or Python).

### Step 3:
1. A Message Authentication Code (MAC) is a cryptographic technique that ensures the integrity and authenticity of a message.
2. The MAC is generated using a secret key and a cryptographic hash function, such as HMAC (Hash-based Message Authentication Code).
3. When a message is received, the MAC can be recalculated and compared with the transmitted MAC to verify the message's authenticity.



## ALGORITHM STEPS:

### **MAC Generation**:
1. Select a secret key shared between the sender and receiver.
2. Use the secret key and the message as inputs to the cryptographic hash function (HMAC).
3. The output of the hash function is the MAC.

### **MAC Verification**:
1. Upon receiving a message and its MAC, the receiver recalculates the MAC using the shared key and received message.
2. If the calculated MAC matches the received MAC, the message is authenticated and has not been altered.



## PROGRAM (Python):

In Python, the `hmac` library can be used to implement HMAC, a widely used type of Message Authentication Code.

### Program:

```python
import hmac
import hashlib

# Function to generate HMAC using a secret key and message
def generate_mac(secret_key, message):
    # Create an HMAC object using the secret key and SHA256 hash function
    mac = hmac.new(secret_key.encode(), message.encode(), hashlib.sha256)
    return mac.hexdigest()

# Function to verify the MAC
def verify_mac(secret_key, message, received_mac):
    calculated_mac = generate_mac(secret_key, message)
    if hmac.compare_digest(calculated_mac, received_mac):
        print("MAC verification successful! The message is authentic.")
    else:
        print("MAC verification failed! The message may have been tampered with.")

def main():
    # Input secret key and message
    secret_key = input("Enter the shared secret key: ")
    message = input("Enter the message to authenticate: ")
    
    # Generate MAC for the message
    mac = generate_mac(secret_key, message)
    print(f"Generated MAC: {mac}")
    
    # Simulate message transmission and MAC verification
    received_mac = input("Enter the received MAC for verification: ")
    verify_mac(secret_key, message, received_mac)

if __name__ == "__main__":
    main()
```



## OUTPUT:

```
Enter the shared secret key: mysecretkey
Enter the message to authenticate: Hello, this is a secure message.
Generated MAC: d2a6d0ecb8ed84fc3b64a028cb4ab0211bfbac1f459b373a3f46041babe5a343
Enter the received MAC for verification: d2a6d0ecb8ed84fc3b64a028cb4ab0211bfbac1f459b373a3f46041babe5a343
MAC verification successful! The message is authentic.
```



## RESULT:
The implementation of the Message Authentication Code (MAC) using HMAC with the SHA-256 hash function was successful. The generated MAC ensures the integrity and authenticity of the message.
