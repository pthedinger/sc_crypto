AES user guide
''''''''''''''

AES (Rijndael) encryption and decryption is performed using the functions
below. Typically, a key is first expanded using the appropriate function
(depending on whether one decrypts or encrypts) and then the stream is
encoded/decoded using ``AESEncryptBlock()`` or ``AESDecryptBlock()``. A convenience
function calls both of these for streams that comprise just a single block.
The AES interface assumes that all data is word-aligned. Character streams
have to be aligned to fit on word boundaries.

Encryption of a single block is performed by calling the funciton
``AESEncrypt()``. If multiple blocks are to be encrypted with an identical
key, the funciton ``AESEncryptKey()`` should be called once followed by
multiple calls to ``AESEncryptBlock()``

Decryption of a single block is performed by calling the funciton
``AESDecrypt()``. If multiple blocks are to be decrypted with an identical
key, the funciton ``AESDecryptKey()`` should be called once followed by
multiple calls to ``AESDecryptBlock()``

API
===

.. doxygenfunction:: AESEncryptBlock

.. doxygenfunction:: AESEncryptExpandKey

.. doxygenfunction:: AESEncrypt

.. doxygenfunction:: AESDecryptBlock

.. doxygenfunction:: AESDecryptExpandKey

.. doxygenfunction:: AESDecrypt



Example
=======


An example program is shown below::

  unsigned int plain[4] = {1,2,3,4};
  unsigned int key[4] = {12314241,4367465,1231244,1234569};
  unsigned int cipher[4];
  main() {
    AESEncrypt(input, key, cipher);
    AESDecrypt(cipher, key, output);
    return 0;
  }
