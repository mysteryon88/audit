# Slither

```sh
slither .
```

```
INFO:Detectors:
KittenRaffle.withdrawFees() (KittenRaffle.sol#195-206) sends eth to arbitrary user
        Dangerous calls:
        - (success,None) = feeAddress.call{value: feesToWithdraw}() (KittenRaffle.sol#203)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#functions-that-send-ether-to-arbitrary-destinations

INFO:Detectors:
KittenRaffle.selectWinner() (KittenRaffle.sol#146-192) uses a weak PRNG: "winnerIndex = uint256(keccak256(bytes)(abi.encodePacked(msg.sender,block.timestamp,block.difficulty))) % players.length (KittenRaffle.sol#157-161)"
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#weak-PRNG

INFO:Detectors:
KittenRaffle.withdrawFees() (KittenRaffle.sol#195-206) uses a dangerous strict equality:
        - require(bool,string)(address(this).balance == uint256(totalFees),KittenRaffle: Currently active players!) (KittenRaffle.sol#196-200)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#dangerous-strict-equalities

INFO:Detectors:
Reentrancy in KittenRaffle.refund(uint256) (KittenRaffle.sol#107-124):
        External calls:
        - address(msg.sender).sendValue(entranceFee) (KittenRaffle.sol#120)
        State variables written after the call(s):
        - players[playerIndex] = address(0) (KittenRaffle.sol#122)
        KittenRaffle.players (KittenRaffle.sol#23) can be used in cross function reentrancies:
        - KittenRaffle.enterRaffle(address[]) (KittenRaffle.sol#83-103)
        - KittenRaffle.getActivePlayerIndex(address) (KittenRaffle.sol#129-138)
        - KittenRaffle.players (KittenRaffle.sol#23)
        - KittenRaffle.refund(uint256) (KittenRaffle.sol#107-124)
        - KittenRaffle.selectWinner() (KittenRaffle.sol#146-192)
Reference: https://github.com/crytic/slither/wiki/Detector-Documentation#reentrancy-vulnerabilities-1
```
