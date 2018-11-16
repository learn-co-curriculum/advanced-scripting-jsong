
# Addresses

P2SH addresses have a very similar structure to P2PKH addresses. Namely, there's 20 bytes that are being encoded with a particular prefix and a checksum that helps identify if any of the characters are wrong encoded in Base58.

Specifically, P2SH uses the 5 byte one mainnet which translates to addresses that start with a 3 in base58.

### Test Driven Exercise

Write methods to translate h160 to p2sh and p2pkh addresses.


```python
def h160_to_p2pkh_address(h160, testnet=False):
    '''Takes a byte sequence hash160 and returns a p2pkh address string'''
    # p2pkh has a prefix of b'\x00' for mainnet, b'\x6f' for testnet
    if testnet:
        prefix = b'\x6f'
    else:
        prefix = b'\x00'
    return encode_base58_checksum(prefix + h160)


def h160_to_p2sh_address(h160, testnet=False):
    '''Takes a byte sequence hash160 and returns a p2sh address string'''
    # p2sh has a prefix of b'\x05' for mainnet, b'\xc4' for testnet
    if testnet:
        prefix = b'\xc4'
    else:
        prefix = b'\x05'
    return encode_base58_checksum(prefix + h160)
```
