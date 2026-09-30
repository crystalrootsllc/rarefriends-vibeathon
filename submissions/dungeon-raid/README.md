# Dungeon Raid

**Project name**
Dungeon Raid

**Builder / contact**
Fresh · [@crystalrootsllc](https://github.com/crystalrootsllc)

**Category**
Character Spotlight

**What did you build?**
A pixel-art dungeon raid: your selected Generations Friend fights **Shade Moth** with Attack / Guard / Rare Beam. Timed Guards charge Rare Beam. Clear Normal (2 bars) or Max (4 bars, optional simulated Shield Bar).

**How does it use Rare Friends?**
You play as your own Generations NFT with its original FriendSDK sprites. The FriendSDK runtime handles wallet connect, owned Friend selection and eligibility (Robinhood mainnet 4663, generation ≥ 1). No custom wallet UI.

**Source code**
[https://github.com/crystalrootsllc/dungeon-raid](https://github.com/crystalrootsllc/dungeon-raid) · FriendSDK **v0.1.2**

Includes `patches/owned-friends.ts` (see Known limitations).

**Playable demo / how to run**
- **GitHub Pages (preferred for judges):** https://crystalrootsllc.github.io/dungeon-raid-preview/
- Tunnel mirror: https://forty-wed-truly-cancelled.trycloudflare.com

Or locally (Node.js 22+): clone the source repo above into `games/familiar-care` inside a FriendSDK v0.1.2 checkout, apply the patch, then `npm ci && npm run build && npm run dev:game -- games/familiar-care`.

Wallet: Robinhood **4663** + hardwired Generations NFT **gen ≥ 1**. Purchases are simulated; no RF funding or live txs required for the preview.

**Judges without a wallet / stuck on Friend loading**
1. Prefer `friendsdk test` / mock wallet (automated fixture) from a FriendSDK checkout.
2. Or open the preview in a mobile wallet in-app browser (MetaMask / Coinbase / Rabby) on chain 4663.
3. Stock FriendSDK 0.1.2 discovery queries `eth_getLogs` from block 0; the public Robinhood RPC caps spans at 10M blocks, so Friend load can fail until `patches/owned-friends.ts` is applied (chunked owner-filtered history from the Generations deploy block).

**How do you play?**
- **OPEN** (lime): Attack the moth.
- **INCOMING** (coral): a ring closes on your Friend — Guard when it turns lime for a timed guard.
- **Rare Beam**: unlocks after 2 timed guards; 5× Attack on OPEN (thick lime beam visual).
- Keys: A / G / R or 1 / 2 / 3. Esc pauses.

**Costs and rewards**
Everything is **simulated** and labeled. Optional Max **Shield Bar** costs **5 RF** (`buy` / `play` / `settle`) and leaves **1 Moth Scale** redeemable for **1 RF**. Net shield cost 4 RF. Expected / max reward: 1 RF per the game.json chance schema.

**What have you tested?**
`friendsdk check`, `friendsdk test` at 960px and 390px, TypeScript check, full Normal + Max (Shield) playthrough bots, phone layout audits at 390×844 and 390×659. Automated checks use the SDK mock wallet fixture.

**Known limitations**
- Leaderboard is **LOCAL** / session-only (SDK sandbox blocks `localStorage`).
- Economy is simulated only.
- Owned-Friends discovery needs the included patch for reliable loads on the public Robinhood RPC; without it Retry may fail with the SDK owner-filtered history error.
- Reduced-motion disables shake / flicker / flashes.

**Credits**
FriendSDK v0.1.2 runtime, frame, sprites and sounds. Boss art, dungeon and combat are original to this entry. No emoji.

**Pitch**
Timed Guard charges Rare Beam. Clear Normal or Max.

**Screenshots**
- `dungeon-title.png` — title / Normal·Max
- `dungeon-fight.png` — Rare Beam mid-fire
- `dungeon-victory.png` — victory + score breakdown
