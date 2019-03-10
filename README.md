# Salden

## Security

In general, in this explanation, it is assumed that you can trust Salden. Salden is open-source, and you can inspect the source code yourself.

All your data is stored inside an encrypted SQLite database using SQLCipher ().

Salden can work with this encrypted database in two different ways (you can choose when you first start Salden):
### 1. Generate a random key for you
Salden will generate a secure, random key for you and encrypt its database with it. It will store this key in encrypted form on your device. The key is encrypted with a key from the Android Keystore. Only Salden can read this key from the Android Keystore. Furthermore, Salden can only access the key from Android Keystore if you have unlocked your device in the past 10 hours.

This enables Salden to do the following things:
a) You don't have to re-authenticate every time you open Salden. Instead, Salden asks the Android Keystore for its key, decrypts the key saved on your device and finally decrypts the database which contains your sensitive information.
b) Salden can notify you about new transactions (as explained in a), Salden can decrypt your database on its own).

You should consider that everyone who can unlock your device, or who gets ahold of your device while it is unlocked, could open Salden to view your bank data or see some notifications about new transactions.

### 2. Work with a key provided by you
If you don't think the approach outlined in 1. is secure, or not secure enough for you (maybe you regularly share your device with someone else) you can tell Salden to not use it.

Instead, you can enter a passphrase which will directly be used to encrypt the database. This passphrase is never stored, and thus has to be entered whenever you open Salden. 

If you choose this option, Salden cannot notify you about new transactions, because it cannot decrypt its database on its own.

