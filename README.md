## What is Diffie Hellman key exchange
Diffie–Hellman key exchange is a method of securely exchanging cryptographic keys over a public channel and was one of the first public-key protocols as conceived by Ralph Merkle and named after Whitfield Diffie and Martin Hellman.In the Diffie–Hellman key exchange scheme, each party generates a public/private key pair and distributes the public key. After obtaining an authentic copy of each other's public keys, Alice and Bob can compute a shared secret offline. The shared secret can be used, for instance, as the key for a symmetric cipher.


## Background

Elliptic Curve Cryptography (ECC) is an approach to public-key cryptography, based on the algebraic structure of elliptic curves over finite fields. ECC requires a smaller key as compared to non-ECC cryptography to provide equivalent security (a 256-bit ECC security has equivalent security attained by 3072-bit RSA cryptography).

## Example 

```
Step 1: Alice and Bob get public numbers P = 23, G = 9

Step 2: Alice selected a private key a = 4 and
        Bob selected a private key b = 3

Step 3: Alice and Bob compute public values
Alice:    x =(9^4 mod 23) = (6561 mod 23) = 6
        Bob:    y = (9^3 mod 23) = (729 mod 23)  = 16

Step 4: Alice and Bob exchange public numbers

Step 5: Alice receives public key y =16 and
        Bob receives public key x = 6

Step 6: Alice and Bob compute symmetric keys
        Alice:  ka = y^a mod p = 65536 mod 23 = 9
        Bob:    kb = x^b mod p = 216 mod 23 = 9

Step 7: 9 is the shared secret.
```

## Implementation 

```py
from random import randint
 
if __name__ == '__main__':
 
    # Both the persons will be agreed upon the
    # public keys G and P
    # A prime number P is taken
    P = 23
     
    # A primitive root for P, G is taken
    G = 9
     
      
    print('The Value of P is :%d'%(P))
    print('The Value of G is :%d'%(G))
     
    # Alice will choose the private key a
    a = 4
    print('The Private Key a for Alice is :%d'%(a))
     
    # gets the generated key
    x = int(pow(G,a,P)) 
     
    # Bob will choose the private key b
    b = 3
    print('The Private Key b for Bob is :%d'%(b))
    
    # gets the generated key
    y = int(pow(G,b,P)) 
     
     
    # Secret key for Alice
    ka = int(pow(y,a,P))
     
    # Secret key for Bob
    kb = int(pow(x,b,P))
     
    print('Secret key for the Alice is : %d'%(ka))
    print('Secret Key for the Bob is : %d'%(kb))
    
```
