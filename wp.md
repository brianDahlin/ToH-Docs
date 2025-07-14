# White Paper: The Time of Heroes

## Introduction

The Time of Heroes is a next-generation platform that brings together premium knowledge sharing, on-chain governance and playful social experimentation. We combine one-on-one expert consultations with a bold new concept—a decentralized “meme-state” DAO—where every participant gains political weight through token holdings and creative engagement.

This white paper outlines:

- The core vision and mission of The Time of Heroes
- The key features of our expert marketplace and token model
- The mechanics of our decentralized Meme-State DAO
- Technical foundations, including smart contracts, vesting and Aragon integration
- Roadmap and governance framework

Our goal is to create an ecosystem that rewards learning, collaboration and humor. By freezing (staking) HERO tokens, users earn “grade” levels that determine their voting power and access to platform features. Influencers and celebrities can be elected to virtual offices—president, minister of memes, TikTok justice—earning DAO-funded salaries and driving platform culture through challenges and proposals.

The Time of Heroes blends real-world expertise, blockchain governance and meme culture into a living social experiment. Welcome to a republic where memes rule, voices matter and every hero can shape the future.

---

## What is “Time of Heroes?”

Time of Heroes is a hybrid marketplace and on-chain ecosystem that lets anyone book one-on-one sessions with top-tier experts, influencers or celebrities—and participate in a playful, governance-driven “meme-state” DAO.

Key elements:

1. **Premium Expert Marketplace**

   - Users browse, filter and book live video or audio consultations.
   - Experts set their own rates ($500–$50 000 per session) and manage availability.
   - Payments are held in a secure escrow contract until the meeting ends.

2. **HERO Token Economy**

   - HERO is an ERC-20 token with capped supply and on-chain vesting.
   - Tokens are used to pay for sessions, join challenges, buy digital goods and tip participants.
   - Staking HERO (“freezing” in your account) grants you a “grade” that translates into voting weight and platform perks.

3. **Meme-State DAO**

   - A decentralized, tongue-in-cheek “state” where token holders vote on proposals, elect influencers to virtual offices (president, minister of memes, TikTok judge) and fund community initiatives.
   - Voting power is based on your grade: the amount of HERO staked and duration of the stake.
   - Elected “officials” receive DAO-funded stipends and run events, challenges and mock legislation.

4. **On-Chain Governance & Transparency**

   - All token minting, vesting schedules and DAO votes run on Ethereum (or compatible EVM chains).
   - We leverage Aragon’s Token Manager, Voting and Finance apps to power proposals, quorums and treasury management.

5. **Social Experiment & Gamification**
   - The platform parodies real-world politics and social norms through memes, challenges and community-driven lawmaking.
   - Users earn points, badges and status upgrades by participating in votes, creating content and mentoring others.

Time of Heroes blends serious knowledge exchange with light-hearted social gaming. It’s a space where learning, governance and meme culture collide—giving everyone a chance to level up, cast votes and shape a witty, decentralized republic.

---

## Considerations

Before diving into implementation details, we must address several high-level factors that shape Time of Heroes:

1. Technical

   - **Scalability**
     - Use Layer-2 rollups solutions (e.g. Optimism, Arbitrum, Unichain) to reduce gas costs.
     - Implement proxy upgrade pattern for evolving contracts without downtime.
   - **Security**
     - Rely on audited Halborn, Sherlock libraries for token, vesting and access control.
     - Conduct third-party audits and on-chain monitoring to detect anomalies.
   - **Interoperability**
     - Support EVM-compatible chains and bridge infrastructure for cross-chain HERO transfers.

2. Governance

   - **Token-based voting**
     - Define clear thresholds for quorum, support and proposer power to avoid deadlocks.
     - Implement time-weighted stakes so long-term holders gain influence without centralizing power.
   - **DAO culture**
     - Balance serious proposals (feature roadmaps, grants) with “meme bills” (fun challenges, art contests).
     - Provide clear guidelines and templates for proposal creation and debate.

3. Regulatory & Compliance

   - **Token classification**
     - Monitor jurisdictional rules on utility vs. security tokens; design HERO to emphasize utility.
   - **KYC/AML**
     - Integrate optional identity checks for high-value transactions or elected “officials.”
   - **Data privacy**
     - Comply with GDPR/CCPA for user profile, booking history and messaging data.

4. User Experience

   - **Onboarding**
     - Smooth guided flows for staking, booking and voting.
     - In-app tutorials and tooltips for DAO mechanics.
   - **Transparency**
     - Dashboard showing staked HERO, grade level and upcoming votes.
     - Public ledger of proposals, election results and treasury flows.

5. Economics & Tokenomics
   - **Inflation control**
     - Cap supply at launch; issue new HERO via community-approved token emissions.
   - **Vesting and cliffs**
     - Prevent immediate dumping by team, advisors or early investors.
   - **Incentive alignment**
     - Reward active participants with bonus airdrops, badges and status perks.

By carefully balancing these considerations, Time of Heroes will deliver a robust, secure and engaging platform—where expert knowledge, on-chain governance and meme culture thrive together.

---

## The Meme-State Republic

The Meme-State Republic is our tongue-in-cheek “government” layer within the Time of Heroes ecosystem. Every staked HERO token grants you a voting grade—your political weight—and unlocks access to unique DAO features. Here’s what makes our Meme-State Republic special:

- **Graded Voting**  
  Users freeze HERO for a chosen period. More tokens + longer lock = higher grade and more voting power for elections and proposals.

- **Elected Meme-Officials**  
  Real influencers and celebrities stand for virtual offices—President, Minister of Memes, TikTok Judge, and more. They campaign, get elected by the community, then earn DAO stipends to run challenges, draft “laws” and host public events.

- **Playful Governance**  
  Serious matters (feature funding, expert grants) sit alongside absurd “bills” (meme contests, avatar dress codes). Every proposal lives onchain, is voted on by grade-weighted ballots, and settles automatically via Aragon’s Voting and Finance apps.

- **Treasury & Salaries**  
  The DAO treasury, funded by platform fees and token emissions, pays salaries to elected officials and bounties to contributors. All flows are transparent onchain.

The Meme-State Republic turns governance into a game—where memes are currency, participation is power, and collective trolling drives real innovation.

---

## Governance

Time of Heroes DAO is powered by Aragon’s modular on-chain governance framework. We use three core Aragon apps—Token Manager, Voting and Finance—to manage token permissions, proposals and treasury flows. All settings and code are public and upgradeable by community vote.

### 1. Token Manager

- **Role**: Registers HERO token, mints/burns, manages holdings
- **Permissions**: Controlled by DAO vote—only the Token Manager app can call `mint` or `burn` on HERO contract
- **Docs**: https://docs.aragon.org/token-manager/1.x/

### 2. Voting (TokenVoting)

- **Role**: Handles proposal creation, voting, execution
- **Voting power**: Based on HERO balance (with optional delegation via ERC20Votes)
- **Configurable parameters**: supportThreshold, minParticipation, minDuration, minProposerVotingPower
- **Modes**: normal (end-of-period tally) or early execution (auto-finalize when outcome locked)
- **Docs**: https://docs.aragon.org/token-voting/1.x/

### 3. Finance

- **Role**: Manages DAO treasury, budget proposals, fund disbursement
- **Integration**: Ties into Token Manager (to check balances) and Voting (to authorize transfers)
- **Workflow**: community proposes expense → DAO votes → Finance pays out on-chain
- **Docs**: https://docs.aragon.org/finance/1.x/

### 4. Governance Process

1. **Proposal**
   - Any token holder above minProposerVotingPower can open a vote (see Voting docs).
   - Proposals include metadata, execution actions (mint, transfer, update settings).
2. **Discussion**
   - All proposals are listed in the on-chain forum.
   - Off-chain chat (e.g. Discord) supports drafts, feedback and debate.
3. **Voting**
   - Grade-weighted ballots (HERO staked + duration) decide outcome.
   - Quorum and threshold ensure broad participation.
4. **Execution**
   - Once passed, actions execute automatically via Aragon’s plugin hooks.
   - Finance app releases funds or calls Token Manager methods.

### 5. Upgrades & Security

- All Aragon apps use upgradeable proxies. Community vote can upgrade logic.
- Core smart contracts (HERO, Vesting, Escrow) are owned by DAO’s Admin role, controlled via Token Manager.
- We follow Aragon’s best practices: multisig backups, time-locks for major changes.
- **Audit**: Aragon’s code is audited and battle-tested; we add our own audits for custom contracts.

By leveraging Aragon, Time of Heroes ensures transparent, flexible and community-driven governance—where every HERO holder has a real voice in building our Meme-State Republic.

---

## Heroes Grants Program

**Funding to support growth of projects in the Time of Heroes ecosystem**

**Experiment. Build. Get Funded.**  
**Submission Open:** 08/01/2025  
**Application Evaluations Begin:** 09/01/2025  
**First Funding Round:** Q4 2025

As part of our commitment to growing the Time of Heroes platform and the wider Web3 community, the Heroes Foundation offers a comprehensive grants program focused on funding development, research, marketing and creative contributions that expand our ecosystem.

The program is open to projects at any stage:

- **Startups** experimenting with new dApps or tools
- **Enterprises** integrating Time of Heroes into their offerings
- **Veteran teams** proposing improvements, tooling or community initiatives

For more details on the Heroes Foundation, see [Foundation Docs].

---

### What is the Heroes Grants Program?

The Heroes Grants Program (HGP) accelerates platform growth by incentivizing projects to build on, with or around Time of Heroes. Grants are awarded by DAO vote from the 20% treasury allocation.

There are three tracks:

#### 1. Ecosystem Grants

Ongoing, open applications for any contribution that benefits ToH.

- **Open Applications:** submit any idea—development, UX improvements, tooling, content.
- **Requests for Proposals (RFPs):** focused calls for specific needs (e.g. UI overhaul, new integrations).
  > See [Ecosystem Grants page] for submission guidelines.

#### 2. RPGF (Retroactive Public Goods Funding)

Rewards projects based on on-chain impact metrics:

- Gas usage, transaction volume
- User growth, stickiness, capital flows
- Qualitative criteria (code quality, documentation)  
  Projects with demonstrated impact may apply retroactively.
  > See [RPGF page] for criteria and metrics.

#### 3. Hackathons

Time-boxed events where developers tackle challenges, build prototypes and win grants.

- In-house ToH hackathons on themes like “Meme-Governance” or “DAO Tooling”
- Co-hosted events with partner communities
- Prize pools funded by the DAO treasury and sponsors
  > See [Hackathons page] for upcoming events and rules.

**How it works:**

1. **Submit proposal** through DAO interface.
2. **Community review** and discussion.
3. **DAO voting** (grade-weighted) to approve funding.
4. **Funds disbursed** via Aragon Finance app.
5. **Milestones tracked** onchain; subsequent tranches released upon completion.

By channeling 20% of our treasury into grants, Time of Heroes empowers builders, creators and meme-innovators to collectively shape our Meme-State Republic.
