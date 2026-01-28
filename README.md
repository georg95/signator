# Signator
0-Dependency airgapped ethereum wallet.

This app can turn spare mobile phone(or laptop) into hardware wallet, that will work like keystone - with QR codes.

You will have view-only Metamask/Rabby wallet on main phone/PC, and signator on separate offline device.

https://georg95.github.io/signator/

<b>WORK IN PROGRESS</b>

- Works 100% offline after install (TODO PWA install button)
- Compatible with Metamask and Rabby wallet
- Supports all EVM chains that share address:
  - Ethereum
  - Binance Smart Chain (BSC)
  - L2s: Arbitrum/Base/Optimism/Polygon
  - USDT/USDC and other tokens on Ethereum/BSC, and L2 chains
  - Ethereum testnets
  - Hardcat local (to test 100% locally)
- Support animated QR codes for large transactions
- (TODO) Decodes transaction and shows what it will actually do - to prevent blindsigning mistakes

## Security:
- No dependencies, all code that is running is in the repo: auditable, reduced supply chain attack surface
- Offline, communication only with QR-codes
- bip39 seed never stored, only single derived private key
- (TODO) Verifiable user-defined entropy to mitigate seed generation attack
- Private key stored encrypted with
  - Very slow to bruteforce hashing function: 600000 rounds of pbkdf2-sha512
  - (TODO) Native secure enclave (if available)
- Sandboxed keyboard and inputs for bip39 seed and password - to prevent leak through system keyboard and input
- Decrypted private key never stored in memory longer than needed to sign transaction and immediately erased
- Seed/private key never stored as strings to prevent leak over memory footprint
- Side channel attack mitigation in secp256k1 multipication
- Standard battle-tested RFC-6979 signature scheme
