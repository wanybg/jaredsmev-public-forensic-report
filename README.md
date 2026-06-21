# jaredsmev-public-forensic-report


JaredFromSubway / @jaredsmev Public Forensic Report

This repository contains an independent defensive forensic report on the public @jaredsmev incident involving the JaredFromSubway MEV infrastructure.

The report is based on public on-chain data and public reporting. It focuses on the apparent approval / transferFrom failure mode, the primary drain transaction, indicators of compromise, a safe Foundry mainnet-fork reproduction plan, approval-seed investigation steps, and defensive hardening recommendations.

No reusable exploit code or attack contract is included.

Scope

This report covers:

* primary drain transaction analysis;
* observed token movements;
* likely approval / transferFrom failure mode;
* indicators of compromise;
* approval-seed investigation methodology;
* safe Foundry mainnet-fork reproduction steps;
* defensive guardrails for MEV executors and searcher pipelines;
* suggested monitoring and incident response actions.

Primary Transaction

0x2be8704f5a59b69e0b71f64aefdb99eb0e8ae9fb3926147c581910d71bcf3e65

Known Addresses

Victim / source:
0x1f2F10D1C40777AE1Da742455c65828FF36Df387
External caller:
0x5aF38735B215b00aa7C9f93fEd7ee415CeCB36e1
Contract called in the primary transaction:
0xb84db016324e8F2BFdD8DD9c260338AEE0A8DF52
Observed receiver:
0x3e37f4A10d771Ba9dE44b6d301410b1BEdeA65d0

Assets Observed

WETH:
0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2
USDC:
0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48
USDT:
0xdAC17F958D2ee523a2206206994597C13D831ec7

Safety Notice

This repository is defensive in nature.

It does not include:

* reusable exploit code;
* malicious Solidity contracts;
* counter-MEV trap code;
* instructions to drain bots or users;
* private exploit reproduction against live funds.

The purpose is to support incident analysis, post-mortem work, and defensive hardening.

Independent Research Note

This work was prepared independently using public data. It is not an official statement from JaredFromSubway, @jaredsmev, Blockaid, Etherscan, or any other third party.

If this report saves time or helps with remediation, voluntary sats are appreciated.

X: @TheRoadTo1BTC
Project: https://roadto1btc.vercel.app
BTC: bc1qc7yc7xrmle9rdygp6xppn222uv26e68ymn4n39

Can the internet help one random person reach 1 BTC?
100,000,000 sats. Public. On-chain. No token. No promises.
