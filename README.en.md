# JPToken-Implementation of ERC 223 token

*Read this in other languages: [English](README.en.md) , [Japanese](README.ja.md) .*

## Overview

This is the source code and document about the token of [ERC223 token standard](https://github.com/ethereum/EIPs/issues/223) issued by [JPToken Crypto-currency project](https://www.jptoken.org/) .

**Token name**

`JPToken`

**Unit of token**

`JPT`

**Number of digits after the decimal point**

`18`

**Total supply amount**

`1,000,000,000.000000000000000000 (JPT)`

## specification

For basic specifications, implement the functions and specifications discussed in the following URL.

[Dexaran / ERC223-token-standard at Recommended](https://github.com/Dexaran/ERC223-token-standard/tree/Recommended)

As an exception, the following functions have not been implemented because they have determined that they may cause unintended operation.

```solidity
  function transfer(address to, uint value, bytes data, string custom_fallback) public returns (bool ok);
```

As an additional specification, it is implemented to check the return value when executing `tokenFallback()` , which is discussed in the following URL. This addresses the loss of tokens due to the fallback function being executed.

https://github.com/ethereum/EIPs/issues/223#issuecomment-423952050

## Test Cases

Check the operation with a test script using [Truffle Suite](https://truffleframework.com/) .

Paste the test execution results below.

```bash
$ truffle test
Using network 'test'.


Compiling your contracts...
===========================
> Compiling ./test/ImplementedERC223Fallback.sol
> Compiling ./test/NotImplementedERC223Fallback.sol
> Compiling ./test/NotImplementedERC223FallbackButHasFallback.sol
> Artifacts written to /var/folders/9y/6q4417_x24b107s0jc7g5gmw0000gp/T/test-119215-62107-oljwve.nornb
> Compiled successfully using:
   - solc: 0.5.0+commit.1d4f565a.Emscripten.clang



  Contract: [TEST] ERC223Token Transfer to EOA
       [LOG] Owner      : 1,000,000,000.000000000000000000
       [LOG] User1      : 0.000000000000000000
       [LOG] User2      : 0.000000000000000000
    ✓ Initial state is the owner address token holding number: 1,000,000,000.000000000000000000 (80ms)
       [LOG] Owner      : 999,999,900.000000000000000000
       [LOG] User1      : 100.000000000000000000
       [LOG] User2      : 0.000000000000000000
    ✓ Transfer to Owner->User1 100.000000000000000000 (133ms)
       [LOG] Owner      : 999,999,700.000000000000000000
       [LOG] User1      : 100.000000000000000000
       [LOG] User2      : 200.000000000000000000
    ✓ Transfer to Owner->User2 200.000000000000000000 (125ms)
       [LOG] Owner      : 999,999,700.000000000000000000
       [LOG] User1      : 100.000000000000000000
       [LOG] User2      : 200.000000000000000000
    ✓ Transfer to User1->User2 200.000000000000000000 (123ms)

  Contract: [TEST] ERC223Token Transfer to contract
       [LOG] implemented: 0.000000000000000000
       [LOG] ImplementedERC223Fallback : 0x8f0483125FCb9aaAEFA9209D8E9d7b9C8B9Fb90F
       [LOG] implemented: 100.000000000000000000
    ✓ Allow token transfer to implemented contract (160ms)
       [LOG] notImplemented: 0.000000000000000000
       [LOG] NotImplementedERC223Fallback : 0x2C2B9C9a4a25e24B174f26114e8926a9f2128FE4
       [LOG] Returned error: VM Exception while processing transaction: revert
       [LOG] notImplemented: 0.000000000000000000
    ✓ Not allow token transfer to no implemented contract (163ms)
       [LOG] hasFallback: 0.000000000000000000
       [LOG] NotImplementedERC223FallbackButHasFallback : 0xFB88dE099e13c3ED21F80a7a1E49f8CAEcF10df6
       [LOG] Returned error: VM Exception while processing transaction: revert
       [LOG] hasFallback: 0.000000000000000000
    ✓ Not allow transfer to has fallback contract (144ms)


  7 passing (1s)
```

## Implementation

Implementation will be released on GitHub.

https://github.com/jptoken-project/jptoken-erc223-implementation

## References

- [Dexaran / ERC223-token-standard at Recommended](https://github.com/Dexaran/ERC223-token-standard/tree/Recommended)

- [ERC223 token standard · Issue # 223 · ethereum / EIPs](https://github.com/ethereum/EIPs/issues/223)
