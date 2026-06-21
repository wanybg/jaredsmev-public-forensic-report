Foundry Mainnet-Fork Reproduction Plan

This document describes a defensive reproduction workflow. It does not include reusable exploit code.

Requirements

* Foundry
* Archive Ethereum RPC
* Access to debug_traceTransaction
* Primary transaction hash

Primary Transaction

export TX="0x2be8704f5a59b69e0b71f64aefdb99eb0e8ae9fb3926147c581910d71bcf3e65"
export ETH_RPC_URL="https://your-archive-rpc"

Basic Inspection

cast tx $TX --rpc-url $ETH_RPC_URL
cast receipt $TX --rpc-url $ETH_RPC_URL
cast run $TX --rpc-url $ETH_RPC_URL

Call Trace

cast rpc debug_traceTransaction $TX '{"tracer":"callTracer","timeout":"120s"}' --rpc-url $ETH_RPC_URL

Allowance Checks at Previous Block

The reported block is 25360696. Check allowances at 25360695.

export VICTIM="0x1f2F10D1C40777AE1Da742455c65828FF36Df387"
export SPENDER="0xb84db016324e8F2BFdD8DD9c260338AEE0A8DF52"
export WETH="0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2"
export USDC="0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48"
export USDT="0xdAC17F958D2ee523a2206206994597C13D831ec7"
cast call $WETH "allowance(address,address)(uint256)" $VICTIM $SPENDER --block 25360695 --rpc-url $ETH_RPC_URL
cast call $USDC "allowance(address,address)(uint256)" $VICTIM $SPENDER --block 25360695 --rpc-url $ETH_RPC_URL
cast call $USDT "allowance(address,address)(uint256)" $VICTIM $SPENDER --block 25360695 --rpc-url $ETH_RPC_URL

Approval-Seed Search

Search historical Approval events where:

owner = 0x1f2F10D1C40777AE1Da742455c65828FF36Df387
spender = 0xb84db016324e8F2BFdD8DD9c260338AEE0A8DF52

Repeat against any spender discovered inside the call trace.

Defensive Validation Goals

A successful defensive reproduction should answer:

1. Which spender had allowance?
2. When was the allowance granted?
3. Was the approval direct or routed through an intermediate contract?
4. Were approvals persistent or temporary?
5. Did the searcher simulation detect allowance deltas?
6. Did the executor enforce spender allowlists?
7. Could a per-token or per-spender cap have limited the loss?
8. Could post-operation allowance cleanup have prevented the final drain?
