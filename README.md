# call

ZeroStyl – Privacy Toolkit for Stylus


Details

ZeroStyl is an open-source Rust-based toolkit to streamline privacy-preserving smart contract development on Arbitrum Stylus (WASM/Rust VM, 10x EVM perf).  I address the "zk-dev friction": only 20% of Stylus apps use zk-SNARKs for privacy in 2025, slowing Arbitrum adoption (TVL +41% YoY) and exposing users to MEV/data leaks ($500M+ losses/year).
Problem:
Stylus lacks native zk-tooling for Rust, forcing manual workflows (hours for circuits). This limits DeFi/gaming privacy apps.
Solution: ZeroStyl delivers:
- zk-Compiler Rust: Compiles halo2 zk-SNARKs to WASM for Stylus contracts (<100ms proofs).
- Privacy Debugger: Tests proofs via zk-mocking (no full sim).
- ABI Exporter zk: Generates privacy-safe interfaces for DeFi (ex. : swaps sans collateral reveal).
Tech implementation:
- Base: Stylus SDK (Rust/WASM) + halo2 for scalable SNARKs.
- Roadmap: Explore zk-STARKs for post-quantum security (FRI-based proofs, 2026 scalability).
Impact: Cuts zk-dev time by 50%, boosts Stylus adoption 30% (1k+ devs, Arbitrum Discord 50k base). Metrics: GitHub downloads, zk-contracts deployed. Aligns Stylus Sprint: Makes Arbitrum zk-L2 leader.
These contracts are from users/developers using the tool - not contracts deploy ourselves.
Risks/Mitigations: zk scalability – mitigated by halo2 optimizations. STARKs complexity – deferred to v2. Timeline: 6 months.
Telegram

@kazai_777

Twitter

@kazai777

What innovation or value will your project bring to Arbitrum? What previously unaddressed problems is it solving? Is the project introducing genuinely new mechanisms

Innovation and Value: ZeroStyl delivers three novel mechanisms:

zk-Compiler Rust: Automates compilation of halo2 zk-SNARKs into WASM for Stylus contracts, enabling <100ms privacy proofs (e.g., tx masking).
Privacy Debugger: Introduces zk-mocking to test proofs without full simulations, cutting dev time by 50%.
ABI Exporter zk: Generates privacy-safe interfaces for DeFi integrations (e.g., swaps without revealing collateral), a first for Stylus.
These tools make zk-development accessible to 1k+ devs (Arbitrum Discord 50k base), boosting Stylus adoption by 30% and positioning Arbitrum as the leading zk-L2 (vs. zkSync). By reducing privacy implementation barriers, ZeroStyl enhances Arbitrum’s competitiveness in privacy-driven DeFi/gaming markets (e.g., $100B+ NFT/gaming by 2027). My experience at Gno.land ensures a polished, dev-friendly toolkit, while my zk-STARKs work informs a roadmap v2 for post-quantum STARKs (2026 scalability).
Unaddressed Problems: ZeroStyl solves the lack of native zk-tooling for Stylus, a gap unaddressed by existing Rust SDKs or EVM-focused zk-libs (e.g., circom standalone). No toolkit currently unifies zk-compilation, debugging, and ABI export for WASM/Stylus, making ZeroStyl a pioneering solution.
New Mechanisms: The zk-mocking debugger and WASM-native SNARK compiler are genuinely new, tailored for Stylus’s Rust ecosystem. These mechanisms, ensure ZeroStyl delivers unmatched value, aligning with Stylus Sprint’s mission to drive high-impact developer tools.

What is the current stage of your project

ZeroStyl is in the pre-development/conceptual stage, with a clear technical design and roadmap ready for execution upon grant approval.

Do you have a target audience? If so, which one

ZeroStyl targets Arbitrum Stylus developers building privacy-preserving DeFi and gaming dApps

Do you know about any comparable protocol, event, game, tool or project within the Arbitrum ecosystem

Comparable projects in the Arbitrum ecosystem include the Stylus SDK (official Rust/WASM tooling for smart contracts, lacking native zk-SNARKs integration) and Renegade (onchain dark pool using Stylus for zk-privacy in DeFi trading). ZeroStyl differentiates by providing a unified zk-compiler, debugger, and ABI exporter specifically for zk-SNARKs development on Stylus, addressing the gap in accessible privacy tooling.

Have you received a grant from the DAO, Foundation, or any Arbitrum ecosystem related program or conducted any IRL like a hackathon or workshop

No

Have you received a grant from any other entity in other blockchains that are not Arbitrum

Yes, from gno.land for the development of a packages and a VSCode plugin for the gno language.

What is the idea/project for which you are applying for a grant

ZeroStyl is an open-source Rust-based toolkit designed to simplify the development of privacy-preserving smart contracts on Arbitrum Stylus (WASM/Rust VM, 10x more performant than EVM). The project addresses the "zk-dev friction": in 2025, only 20% of Stylus apps integrate zk-proofs for privacy, limiting Arbitrum adoption in DeFi and gaming (TVL +41% YoY) and exposing users to data leaks/MEV (losses >$500M USD/year). Current tools like the cargo-stylus CLI lack native zk support, forcing time-consuming manual workflows (hours for circuits).

ZeroStyl's innovation relies on three unique mechanisms:

zk-Compiler Rust: Compiles zk-SNARKs circuits (via halo2) into WASM for Stylus contracts, generating proofs <100ms (e.g., masking tx data).
Privacy Debugger: Tests proofs via zk-mocking (simulation without full execution), reducing debug time by 50%.
zk ABI Exporter: Generates privacy-safe ABI interfaces for DeFi integrations (e.g., swaps without revealing collateral).
Details :

The zk-ABI Exporter is a code generation tool that creates privacy-preserving Application Binary Interfaces (ABIs) for Stylus contracts using zero-knowledge proofs, enabling DeFi protocols to interact with private data without compromising confidentiality.

How the zk-ABI Exporter works:

Core Mechanism:

Source Code Parsing: Scans Stylus contract Rust code for parameters marked with #[zk_private] attribute macro

Automatic Circuit Generation: For each private parameter, generates a corresponding halo2 circuit with:

Public inputs: commitment hash, validity constraints
Private inputs (witness): actual parameter value, randomness nonce
Circuit constraints: proves Hash(private_value, nonce) == commitment AND private_value satisfies_condition
ABI Transformation: Replaces private parameters in function signatures with:

commitment: Bytes32 (Pedersen hash of the private value)
zk_proof: Bytes (SNARK proof, ~200 bytes compressed)
SDK Generation: Exports client libraries in multiple languages:

TypeScript/JavaScript (for web3.js, ethers.js)
Rust (for native Stylus contract interactions)
Python (for backend services, data analysis)
These tools unify zk compilation, debugging, and export, making zk development accessible to Rust/Stylus developers without advanced mathematical expertise. The project is early-stage (pre-development), with validated architecture (Rust input → halo2 SNARK → WASM Stylus) and MIT license for open-source adoption.

Implementation Plan:

The implementation leverages mature libraries (Stylus SDK for Rust/WASM, halo2 for scalable SNARKs).

Timeline:

6 months, divided into 3 milestones, with progressive deployment on Arbitrum Sepolia testnet.

Tech Stack:

Rust crates (halo2_proofs, stylus_sdk); unit tests (100% coverage); GitHub integration for community contributions.
Phases:

M1 (months 1-2): Focus on basic compiler
M2 (months 3-4): Add debugger with on-chain tests
M3 (months 5-6): Exporter + public launch (npm/pypi, docs).

Outline the major deliverables you will obtain with this grant

ZeroStyl will deliver concrete and measurable artifacts:

M1 (Months 1-2): Rust crate for zk-compiler (2 example circuits: tx privacy, state mask); local Stylus tests; 5-min demo video; GitHub push (100% coverage).
Details :

The zk-Compiler Rust crate (Milestone 1) is a core library that automates the compilation of zero-knowledge proof circuits written in Rust (using the halo2 proving system) into WASM bytecode compatible with Arbitrum Stylus contracts.
Technical Architecture:

Input: Rust code defining zk-SNARK circuits (using halo2_proofs crate, v0.3+)
Processing: The compiler parses circuit logic, optimizes constraint systems using Plonk-based arithmetization, and generates proving/verification keys
Output: WASM module deployable on Stylus with proof generation functions callable from smart contracts
Integration: Compatible with stylus-sdk v0.9.0+ and follows Arbitrum's WASM pricing model (ink-based computation)

The 2 Example Circuits:

Transaction Privacy Circuit (tx_privacy):

Purpose: Masks transaction amounts and sender/receiver identities in token transfers

Technical Implementation:

Uses Pedersen commitments for amount hiding: commitment = PedersenHash(amount, randomness)
Merkle tree membership proofs (depth 32) for account verification
Proves: "I own UTXO at index i with value V ≥ transfer_amount" without revealing i or V
Use Cases:

Private DeFi lending (hide collateral amounts from liquidation bots)
Confidential DAO voting (prove token holdings without revealing exact balance)
Anonymous token swaps (similar to Renegade's dark pool model on Arbitrum)
State Mask Circuit (state_mask):

Purpose: Hides sensitive smart contract state variables while proving compliance with conditions

Technical Implementation:

Range proofs: Prove collateral_ratio ∈ [150%, 300%] without revealing exact value.
Comparison gates: Verify hidden_balance > threshold using constraint-based arithmetic.
State commitments: state_commit = Hash(state_value, nonce) stored on-chain.
Use Cases:

Privacy-preserving liquidation protection (prove solvency without exposing positions)

Confidential trading strategies (Renegade-style order book privacy)

Regulatory compliance (prove KYC status without revealing identity)

M2 (Months 3-4): CLI debugger with zk-mocking; Stylus SDK integration; 5 zk contracts tested on Sepolia; feedback via Arbitrum forum.

M3 (Months 5-6): zk-safe ABI exporter; complete Rust docs/tutorials; npm/pypi publication; STARKs study (post-quantum); mock DeFi integration; survey of 50 devs (target 200+ GitHub stars). All open-source, and promoted via Arbitrum Discord/forums for immediate adoption.

Please explain how your idea/project aligns with the Arbitrum ecosystem goals

ZeroStyl aligns perfectly with Arbitrum's objectives:

Developer Tools: As a Stylus-native toolkit, it boosts dev productivity (50% zk time reduction), aligned with Stylus Sprint ($5M ARB for high-impact tooling). Unlike EVM-focused SDKs, ZeroStyl makes zk accessible for Rust devs, accelerating scalable dApp development.
DeFi Dominance: Privacy tools (SNARKs for masked tx) strengthen DeFi security on Arbitrum (e.g., lending/swaps without leaks, Aave-like integrable), contributing to TVL dominance (+41% YoY).
Ecosystem Expansion: By onboarding 1k+ devs (50k Discord base), ZeroStyl expands the ecosystem toward privacy-driven gaming/DeFi ($100B+ NFT/gaming market 2027), attracting builders from zkSync/Polygon. We will do this with workshops, complete tutorials, complete and detailed documentation, medium articles, X content, SEO

What is your requested grant

I am requesting $47,000 USD.

Website

N/A

Please provide a detailed breakdown of the budget in term of utilizations, costs and other relevant information

Total Requested Grant: $47,000 USD. No team hires, physical rentals, external vendors, or liquidity/incentive programs are required. Free libraries (halo2, Stylus SDK) and lightweight infrastructure (Arbitrum Sepolia testnet, GitHub Actions) ensure cost efficiency.

Budget Breakdown by Milestone (following Arbitrum DAO economic template):

Milestone 1 (Completion: Month 2, Total: $15,880 USD)

Personnel/Team Costs: $15,880 USD. Links/Resources: GitHub (free), halo2 (open-source), Stylus SDK (free). Estimated Number of Hours: 245. Number of Resources: 1 (solo dev). Justification: Solo dev time for zk-compiler prototype (Rust crate, 2 SNARK circuits). Leverages gno.land tooling experience. 245 hours = ~6 weeks full-time at 40h/week.
Infrastructure/Software Licenses: $0. Links/Resources: Arbitrum Sepolia testnet (free tier). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Free testnet access; no licenses needed (open-source libs).
Equipment/Materials: $0. Links/Resources: N/A. Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: No physical equipment; uses existing dev setup.
Marketing/Outreach: $0. Links/Resources: Arbitrum Discord/Forums (free). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Initial community push via free channels; no outreach costs.
Other Expenses: $0. Links/Resources: N/A. Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: No additional costs (e.g., travel, vendors).
Milestone 2 (Completion: Month 4, Total: $15,960 USD)

Personnel/Team Costs: $15,960 USD. Links/Resources: GitHub (free), halo2 (open-source), Stylus SDK (free). Estimated Number of Hours: 245. Number of Resources: 1 (solo dev). Justification: Solo dev time for privacy debugger (CLI, zk-mocking, 5 contracts on Sepolia). 245 hours = ~6 weeks full-time.
Infrastructure/Software Licenses: $0. Links/Resources: Arbitrum Sepolia testnet (free tier), AWS (free tier). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Free tiers cover gas fees and cloud testing; no licenses.
Equipment/Materials: $0. Links/Resources: N/A. Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: No physical needs.
Marketing/Outreach: $0. Links/Resources: Arbitrum Discord/Forums (free). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Community feedback collection; no outreach costs.
Other Expenses: $0. Links/Resources: N/A. Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: No additional costs.
Milestone 3 (Completion: Month 6, Total: $15,160 USD)

Personnel/Team Costs: $15,160 USD. Links/Resources: GitHub (free), halo2 (open-source), Stylus SDK (free). Estimated Number of Hours: 195. Number of Resources: 1 (solo dev). Justification: Solo dev time for ABI exporter, docs, mock DeFi integration, and STARKs study. Reduced hours (195 = 5 weeks) to balance budget; leverages hackathon zk-STARKs exp.
Infrastructure/Software Licenses: $0. Links/Resources: Arbitrum Sepolia testnet (free tier), AWS (free tier). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Free tiers suffice for final tests/integration.
Equipment/Materials: $0. Links/Resources: N/A. Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: No physical requirements.
Marketing/Outreach: $0. Links/Resources: Arbitrum Discord/Forums (free). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 0. Justification: Adjusted to $0; promotion via free forums and GitHub for adoption.
Other Expenses: $4,000 USD. Links/Resources: Trail of Bits (audit vendor). Hourly Rate: N/A. Estimated Number of Hours: 0. Number of Resources: 1 (external audit). Justification: zk-circuit audit ($4k, industry standard); no other costs.
UPDATE : After researching current audit market pricing, I must transparently correct my initial $4,000 budget allocation. This amount is insufficient for a Trail of Bits audit of zk-circuit cryptography. I will continue my research to obtain different quotes, but part of the grant will necessarily be allocated to an audit.

Grand Total: $47,000 USD.

Provide a list of the milestones, with the USD amount of the grant associated to it, the deliverables that will be provided, and the estimated completion time

Milestone 1: Completion: Month 2. Deliverables: Rust crate for zk-compiler (halo2-to-WASM); 2 example SNARK circuits (tx privacy, state mask); local Stylus tests; GitHub push (100% test coverage); 5-min demo video.
Milestone 2: Completion: Month 4. Deliverables: CLI privacy debugger with zk-mocking; Stylus SDK integration; 5 zk-contracts tested on Sepolia testnet; Arbitrum forum feedback report.
Milestone 3: Completion: Month 6. Deliverables: zk-safe ABI exporter; full Rust docs/tutorials; npm/pypi publication; mock DeFi integration; STARKs feasibility study; 50-dev impact survey.

Are milestones clearly defined, time-bound, and measurable with quantitative metrics where applicable? What are your reference KPI, if applicable, for each milestone

Yes, milestones are clearly defined (specific deliverables like code crates/demos), time-bound (2-4-6 months total), and measurable with quantitative metrics (e.g., GitHub coverage %, # contracts tested). KPIs per milestone:

M1: 100% test coverage (GitHub metrics); 1+ example circuits functional (demo verification).
M2: 50% zk-dev time reduction (internal benchmark vs. manual circuits); 5 contracts deployed (on-chain tx hashes).
M3: 200+ GitHub stars (social metric); 80% positive survey feedback (50 responses); 1 mock integration live (testnet link).

What is the estimated maximum time for the completion of the project

6 months (end of Month 6), aligning with the 6-month grant limit.

How should the Arbitrum community measure the success of this grant

Success measured via:

Adoption KPIs: GitHub stars/downloads (>200 stars, >500 downloads in 3 months post-M3); # zk-contracts deployed using ZeroStyl (>50 on mainnet in 6 months).
Impact Metrics: Dev time reduction (50%, via post-launch survey of 50+ devs); Community feedback (80% positive on Arbitrum forums/Discord).
Ecosystem Growth: Increased Stylus zk-apps (track via Arbitrum explorer, targeting 10% rise in privacy txs); Open-source contribs (>10 PRs in first quarter). Community verifies via GitHub repo, testnet deploys, and surveys.
Primary Method - On-Chain Event Tagging:

ZeroStyl-powered contracts emit standardized events: ZeroStylPrivacyTransaction(contractAddress, operationType, timestamp, version)
Indexed via The Graph subgraph for real-time tracking
Public dashboard at dashboard.zerostyl.dev
Secondary Method - Bytecode Fingerprinting:

Scan Arbitrum mainnet for contracts importing zerostyl-runtime library
Pattern matching on unique WASM signatures from our compiler
Gas consumption analysis
Tertiary Method - Voluntary Registry:

GitHub-based ecosystem registry where developers register contracts
Incentivized with featured placement and marketing support
Current Privacy TX Baseline - Honest Assessment:
We acknowledge: Precise baseline data does NOT currently exist because:

Privacy on Arbitrum is still in early stages with only a few privacy-focused applications present;

Our Research-Based Estimate:

Current Arbitrum privacy TXs: ~800-1,500 per day (estimated from Renegade dark pool activity and other privacy protocols ArbitrumMedium)
Manual analysis: <5% of top 100 Stylus contracts currently use zk-privacy features
Baseline uncertainty: Out of 3.4 million daily Arbitrum transactions Arbitrum Statistics 2025: Latest Metrics, Insights & Trends • CoinLaw, privacy subset is unmeasured.

Measurement Methodology:

Direct attribution via event emissions + bytecode analysis
Open-source tracking scripts published on GitHub
Monthly transparency reports on Arbitrum Forum with Arbiscan links
Third-party verification via Dune Analytics dashboard

What is the economic plan for maintaining operations or continuing the growth of your project after the grant period

Post-grant (after 6 months), ZeroStyl will sustain via open-source model: community contributions (GitHub bounties from ecosystem funds like Arbitrum DAO), partnerships (e.g., Lit Protocol for zk-oracle integrations, generating rev-share), and optional premium features (e.g., enterprise audits at $5k/contract). No ongoing ops costs (solo, free infra); growth via Arbitrum hackathons (e.g., Stylus Sprint extensions) and DeFi protocol sponsorships (e.g., Aave for privacy tools). v2 (STARKs) funded by follow-on grants (e.g., Optimism/Polkadot) or token airdrops if DAO-integrated. Target: Self-sustaining via 1k+ active devs, with 20% annual contrib growth.

Market Needs: For developers building apps and interfaces, what specific challenges or opportunities do they face in Arbitrum

Developers building apps and interfaces on Arbitrum face challenges like the lack of native zk-privacy tooling for Stylus (WASM/Rust VM), forcing manual zk-circuit workflows that take hours and limit scalability (only 20% of Stylus apps use zk-proofs in 2025). This hinders privacy-driven DeFi/gaming dApps (TVL +41% YoY, $500M+ MEV losses), where efficient zk-integration is critical. Opportunities include Arbitrum’s growing ecosystem (Discord 50k+ devs) and Stylus’s 10x EVM performance, enabling innovative, high-performance apps if tooling gaps are addressed. ZeroStyl targets these needs by simplifying zk-development, unlocking privacy features for developers.

Composability: How can your proposed developer tooling (existing or new) facilitate seamless interaction between different protocols and tools built on Arbitrum, the Nova ecosystem and other Orbit chains

ZeroStyl’s zk-compiler, privacy debugger, and ABI exporter enable seamless composability by standardizing zk-SNARKs integration across Arbitrum, Nova, and Orbit chains. The ABI exporter generates privacy-safe interfaces (e.g., for DeFi swaps), allowing protocols like Aave or Uniswap to interact with ZeroStyl-powered contracts on any chain. The debugger’s zk-mocking ensures cross-chain contract testing (e.g., Nova’s low-cost txs with Orbit’s custom L3s), while the compiler’s WASM output supports Stylus’s interoperable architecture. This fosters modular dApp development, enhancing ecosystem synergy (e.g., Orbit chain DeFi composable with Arbitrum One).

Adoption: If your grant focuses on a Growth or Orbit Chain developer tool, how would you ensure its widespread adoption within the developer community

To ensure widespread adoption, ZeroStyl will be open-source (MIT license) with a public GitHub launch, targeting 1k+ Arbitrum devs (50k Discord base). I’ll host free tutorials on Arbitrum forums/Discord/Youtube. Partnerships with Lit Protocol (zk-oracles) and DeFi protocols GMX, Radiant and Camelot DEX will drive integration, while a 50-dev survey post-launch will refine usability, aiming for 200+ GitHub stars and 500+ downloads within 3 months.

If working on Orbit Chain Onboarding and Tooling: How would you adapt your existing developer tooling (or propose a new tool) to simplify building applications on custom Arbitrum Layer 3 chains (Orbit Chains)

For Orbit Chain onboarding, ZeroStyl will adapt its zk-compiler and ABI exporter to support custom L3 configurations (e.g., varying gas models, chain-specific WASM optimizations). A new module, the Orbit zk-Adapter, will map Stylus SNARKs to Orbit chain parameters (e.g., custom proof verification), simplifying cross-L3 deployment.

Instagram

N/A

If applying for a growth oriented grant: Please provide success metrics for the grant with milestone-oriented disbursements

As a growth-oriented grant, success metrics for ZeroStyl include:

Milestone 1 (zk-Compiler Prototype, $15,880 USD, Month 2): 100% test coverage (GitHub metric); 1+ functional circuits (demo verification).
Milestone 2 (Privacy Debugger Integration, $15,960 USD, Month 4): 50% zk-dev time reduction (internal benchmark); 5 contracts deployed (on-chain tx hashes).
Milestone 3 (Toolkit Launch and STARKs Study, $15,160 USD, Month 6): 200+ GitHub stars; 80% positive survey feedback (50 devs); 1 mock integration live (testnet link).
Disbursements: 50% upfront for M1.

LinkedIn

https://fr.linkedin.com/in/zakaria-chaikhi-55907b2a0

Discord

@kazai777

Others

https://github.com/kazai777

Do you acknowledge that your team will be subject to a KYC requirement

Yes

Do you acknowledge that, in case of approval, you will have to provide a report at the completion of the grant and, three months later, complete a survey about your experience

Yes

Team experience and completeness

Gno.land (solo grant): Built multiple packages and a VSCode plugin for Gno (Go-based smart contract language), enhancing developer productivity with open-source tooling (public GitHub repos).

L2 based on ICP (solo architecture design): Developed a zk-STARKs-based transaction anonymization solution (cryptographic pool) for a layer 2, enabling private txs with post-quantum security. Expertise in STARKs circuits informs ZeroStyl’s roadmap v2 for future-proofing.

Solo Lead Developer :

Full-time 6-month commitment dedicated exclusively to ZeroStyl development and delivery.

ZeroStyl = focused toolkit (not full protocol), modular architecture enables sequential development
6-month timeline = +1,000 hours

Category

Developer Tooling
