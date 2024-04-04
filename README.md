# AI Arena Mitigation Review details
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

## Overview of changes

Fixed issues with tokenId restrictions: There was an issue when re-rolling for fighters with token IDs greater than 255 which has been addressed.

Override fixes in safeTransferFrom

DNA generation fixes: Issues in the generation process during minting from the merging pool and in the re-roll and claim functions have been fixed.

Non-transferable GameItems fix: There was a bug that allowed non-transferable game items to be transferred, which has been fixed.

Mitigation of reentrancy in claimRewards: Reentrancy attack was mitigated.

Uninitialized numElements variable: An uninitialized variable numElements was fixed.

ECRecover vulnerability: A known vulnerability with ECRecover was addressed.

Update to ranking and staking mechanisms: There were fixes to staking requirements and an update to ranked battle contracts.

Areas of specific concern would be:

Reentrancy vulnerabilities.
Signature malleability in ECRecover.
Non-transferable items being transferred.

## Mitigations to be reviewed

### Branch
[Mitigations branch](https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/15)

### Individual PRs

| URL | Mitigation of | Original Issue | Purpose | 
| ----------- | ------------- | ----------- | ----------- |
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/1 | H-06 | #68 | Fixed reRoll for fighters with tokenIds greater than 255 | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/2 | H-01 Dupe | #739 | Fixed safeTransferFrom override with data | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/3 | M-05 Dupe | #578 | Fix dna generation in mintFromMergingPool | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/4 | H-02 | #575 | fixed Non-transferable GameItems being transferred with GameItems::safeBatchTransferFrom | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/5 | QA-1 | #48 | Mitigated claimRewards reentrancy, fixed uninitialized numElements and fixed points intialization to match maxId | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/8 | QA-2 | #507 | Fixed Ecrecover is known to be vulnerable to signature malleability | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/9 | M-06 | #137 | Mititgation for NFTs can be transferred even if StakeAtRisk remains, so the user's win cannot be recorded on the chain due to underflow, and can recover past losses that can't be recovered(steal protocol's token) | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/10 | H-03 | #366 | Mitigation for Players have complete freedom to customize the fighter NFT when calling redeemMintPass and can redeem fighters of types Dendroid and with rare attributes | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/11 | M-05 Dupe | #1017 | Updated dna generation in reRoll and updated dna generation in claimFighters | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/12 | M-04 | #868 | Mitigation for DoS in MergingPool::claimRewards function and potential DoS in RankedBattle::claimNRN function if called after a significant amount of rounds passed.| 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/13 | QA-3 | #704 | Mititgated QA Report for #704 | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/14 | QA-4 | #1490 | Mitigated unstakeNRN and setNewRound and mint upto MAX_SUPPLY | 
| https://github.com/ArenaX-Labs/2024-02-ai-arena-mitigation/pull/15 |  | N/A | Admin setup function and new require conditions for staking and unstaking. Unstaking require correction | 

## Out of Scope

N/A
