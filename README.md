# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC
```
GEERTHIVASH J.D. - 212223060067
```
## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:

```
#include <stdio.h>
#include <string.h>
unsigned long simple_hash(const char *data) {
unsigned long hash = 5381;
int c;
while ((c = *data++))
hash = ((hash << 5) + hash) + c; // hash * 33 + c
return hash;
}
unsigned long compute_mac(const char *key, const char *message) {
char combined[400];
strcpy(combined, key);
strcat(combined, message);
return simple_hash(combined);
}
int main() {
char key[100], message[200];
unsigned long mac_sender, mac_receiver;
printf("Enter Secret Key: ");
scanf("%s", key);
printf("Enter Message: ");
scanf("%s", message);
mac_sender = compute_mac(key, message);
printf("\nGenerated MAC: %lu\n", mac_sender);
mac_receiver = compute_mac(key, message);
if (mac_sender == mac_receiver)
printf("✅ Message is Authentic and Unchanged.\n");
else
printf("❌ Message has been Tampered or Key is Wrong.\n");
return 0;
}
```

## Output:
<img width="604" height="234" alt="image" src="https://github.com/user-attachments/assets/6d70ccb3-9c46-4fc8-acc6-3d19fd815a83" />


## Result:
The program is executed successfully.
