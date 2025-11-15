Base-Learn-1-Deployment-Exercise

Base Learn #1 배포 연습 (Deployment Exercise)

📋 지침 (Instructions):

오버플로우/언더플로우 오류 처리 기능을 포함하는 BasicMath 스마트 계약을 배포하세요.

계약 제출처 (Submit Contract Here)

https://docs.base.org/learn/deployment-to-testnet/deployment-to-testnet-exercise

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract BasicMath {

    function adder(uint _a, uint _b) public pure returns (uint sum, bool error) {
        // Use `unchecked` to allow overflow
        unchecked {
            uint c = _a + _b;
            // If the sum result is less than _a, it means an overflow occurred
            if (c < _a) {
                return (0, true);
            }
            return (c, false);
        }
    }

    function subtractor(uint _a, uint _b) public pure returns (uint difference, bool error) {
        // Manually check if underflow will occur (when _a is less than _b)
        if (_a < _b) {
            return (0, true);
        }
        
        // Use `unchecked` to avoid Solidity's underflow check which would revert the transaction
        unchecked {
            uint c = _a - _b;
            return (c, false);
        }
    }
}

