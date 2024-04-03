# AI Arena audit details
- Total Prize Pool: $21,000 in USDC
  - HM awards: $18,000 in USDC
  - Judge awards: $3,000 in USDC
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2024-04-ai-arena-mitigation/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts April 8, 2024 20:00 UTC
- Ends April 15, 2024 20:00 UTC

## Important note 

Each warden must submit a mitigation review for *every High and Medium finding* from the parent audit that is listed as in-scope for the mitigation review. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all High and Medium issues will be considered in-scope and listed here.

- [H-01: A locked fighter can be transferred; leads to game server unable to commit transactions, and unstoppable fighters](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/1709)
- [H-02: Non-transferable GameItems can be transferred with GameItems::safeBatchTransferFrom(...)](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/575)
- [H-03: Players have complete freedom to customize the fighter NFT when calling redeemMintPass and can redeem fighters of types Dendroid and with rare attributes](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/366)
- [H-04: Since you can reroll with a different fighterType than the NFT you own, you can reroll bypassing maxRerollsAllowed and reroll attributes based on a different fighterType](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/306)
- [H-05: Malicious user can stake an amount which causes zero curStakeAtRisk on a loss but equal rewardPoints to a fair user on a win](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/116)
- [H-06: FighterFarm:: reroll won't work for nft id greator than 255 due to input limited to uint8](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/68)
- [H-07:Fighters cannot be minted after the initial generation due to uninitialized numElements mapping](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/45)
- [H-08: Player can mint more fighter NFTs during claim of rewards by leveraging reentrancy on the claimRewards() function](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/37)

- [M-01: Almost all rarity rank combinations cannot be, and are not uniformly, generated](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/1979)
- [M-02: Minter / Staker / Spender roles can never be revoked`..,](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/1507)
- [M-03: Fighter created by mintFromMergingPool can have arbitrary weight and element](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/932)
- [M-04: DoS in MergingPool::claimRewards function and potential DoS in RankedBattle::claimNRN function if called after a significant amount of rounds passed.](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/868)
- [M-05: Can mint NFT with the desired attributes by reverting transaction](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/376)
- [M-06: NFTs can be transferred even if StakeAtRisk remains, so the user's win cannot be recorded on the chain due to underflow, and can recover past losses that can't be recovered(steal protocol's token)](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/137)
- [M-07: Erroneous probability calculation in physical attributes can lead to significant issues](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/112)
- [M-08: Burner role can not be revoked](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/47)
- [M-09: Constraints of dailyAllowanceReplenishTime and allowanceRemaining during mint() can be bypassed by using alias accounts & safeTransferFrom()](https://github.com/code-423n4/2024-02-ai-arena-findings/issues/43)

[ ⭐️ SPONSORS ADD INFO HERE ]

## Overview of changes

Please provide context about the mitigations that were applied if applicable and identify any areas of specific concern.

## Mitigations to be reviewed

### Branch
[ ⭐️ SPONSORS ADD A LINK TO THE BRANCH IN YOUR REPO CONTAINING ALL PRS ]

### Individual PRs
[ ⭐️ SPONSORS ADD ALL RELEVANT PRs TO THE TABLE BELOW:]

Wherever possible, mitigations should be provided in separate pull requests, one per issue. If that is not possible (e.g. because several audit findings stem from the same core problem), then please link the PR to all relevant issues in your findings repo. 

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/your-repo/sample-contracts/pull/XXX | H-01 | This mitigation does XYZ | 

## Out of Scope

Please list any High and Medium issues that were judged as valid but you have chosen not to fix.
