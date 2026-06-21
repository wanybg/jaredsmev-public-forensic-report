Indicators of Compromise

Primary Transaction

0x2be8704f5a59b69e0b71f64aefdb99eb0e8ae9fb3926147c581910d71bcf3e65

Addresses

Victim / Source

0x1f2F10D1C40777AE1Da742455c65828FF36Df387

External Caller

0x5aF38735B215b00aa7C9f93fEd7ee415CeCB36e1

Contract Called in Primary Transaction

0xb84db016324e8F2BFdD8DD9c260338AEE0A8DF52

Observed Receiver

0x3e37f4A10d771Ba9dE44b6d301410b1BEdeA65d0

Tokens

WETH

0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2

USDC

0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48

USDT

0xdAC17F958D2ee523a2206206994597C13D831ec7

Selector Observed

0xc269a509

Investigation Priority

The key open forensic question is to identify the approval-seed transaction that authorized the relevant spender or spender chain to move assets from the affected executor.

Recommended search pattern:

Approval(owner = affected_executor, spender = suspicious_contract)
Transfer(from = affected_executor, to = observed_receiver)
transferFrom(affected_executor, observed_receiver, amount)
