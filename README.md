# 🐹 Squeek Explorer

Live explorer and Squeek dashboard for [Squeekchain](https://squeekchain.com) on Sepolia — **https://squeekexplorer.xyz**

squeekchain-project: 76968b96-8afb-4b36-a60d-786110553b6e

## What it does

**Watch the chain**
- Hamster status (running/idle, rpm, speed), block height and progress to the next block, difficulty, total work, last settled round
- SQK supply, total SQK staked, Squeek supply and Squeeks burned by merges
- Live on-chain activity feed (rewards claimed/staked, merges, deposits, checkpoints) with Blockscout links
- The live deployment's contract list

**Use your Squeeks** (connect MetaMask/Rabby on Sepolia)
- See your Squeeks' on-chain artwork (rendered from `tokenURI`), in your wallet and staked, with level and merge-cooldown badges; hover for traits
- Rewards estimate: your share of all staking power, SQK per day while a reward stream runs, and how the ready merges would change it
- Remembers your wallet and reconnects on return; warns and switches if you're not on Sepolia
- Errors in plain English (e.g. "Squeek #5888 is on merge cooldown, 3,000 blocks to go") instead of raw revert codes
- Stake and unstake Squeeks (`deposit` / `withdraw`, with the one-time approval handled for you)
- Merge two Squeeks (first selected survives, second is burned into it)
- Claim SQK rewards, claim & stake, stake SQK (approval handled), send SQK

**Merge planner**
- Pairs your same-level Squeeks that are past their merge cooldown, in your wallet or in staking (staked pairs merge in place through `mergeDeposited`, no unstaking)
- Shows the power each merge adds, how many blocks until the next Squeek comes off cooldown, and when a wallet/staked split is blocking a pair
- "Full ladder": how far your Squeeks can climb if you keep merging, the highest level you'd reach and the total power gained
- One-click merge for every ready pair; rules (same level, below L10, cooldown vs. Squeekchain height, merges open) come from the contracts' verified source
- Look up any address read-only

Every transaction is simulated with `eth_call` first: if it would revert you see why, and your wallet is never asked to sign it. Keys never touch the site.

## Follows reinstalls on its own

Contract addresses aren't hard-coded. The page reads the live deployment from `api.squeekchain.com/v1/events` and finds the token, collection, staking, dispenser, mining and core contracts wherever the API keeps them, so it kept working through the November 2026 redeploy.

## Run it

It's one static `index.html` with no build step and no dependencies: open it in a browser or serve the folder.
