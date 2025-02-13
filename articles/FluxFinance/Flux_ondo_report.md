# Asset Risk Assessment: Ondo and Flux Finance (OUSG)

## A look into the utility and challenges of tokenizing U.S. Treasuries


Resources (Useful links):

* [Proposal to add fUSDC-fDAI to the Curve Gauge Controller](https://gov.curve.fi/t/proposal-to-add-fusdc-fdai-to-the-curve-gauge-controller/9098)
* [Flux finance website](https://fluxfinance.com/)
* [Flux Finance documentation](https://docs.fluxfinance.com/)
* **Legal docs** - [Terms of Services](https://docs.fluxfinance.com/legal/terms-of-service), [Privacy Policy](https://docs.fluxfinance.com/legal/privacy-policy), [CoinList Risk factors](https://docs.fluxfinance.com/legal/coinlist-risk-factors), [Cookies policy](https://docs.fluxfinance.com/legal/cookies-policy)
* [Github Flux finance](https://github.com/flux-finance)
* [DefiLlama - Flux Finance](https://defillama.com/protocol/flux-finance)
* [Flux Finance audit](https://code4rena.com/reports/2023-01-ondo/) (additional to Compound “reputation”)
* [Flux Finance Bug Bounty on ImmuneFi](https://immunefi.com/bounty/fluxfinance/)
* Flux Finance - [governance forum](https://forum.fluxfinance.com/)
* [Flux finance blog](https://blog.fluxfinance.com/)
* [Ondo Finance website](https://ondo.finance/)
* [Ondo Finance - OUSG](https://ondo.finance/ousg)
* [Ondo Finance docs](https://docs.ondo.finance/)
* [Ondo DAO - Tally](https://www.tally.xyz/gov/ondo-dao)
* [Compound cTokens docs](https://docs.compound.finance/v2/ctokens/#ctokens)
* [MakerDAO Proposal (MIP119)](https://forum.makerdao.com/t/mip119-onboard-dai-funds-to-the-flux-finance-dai-lending-pool/19885)
* [Curve DAO Proposal (Gauge proposal)](https://gov.curve.fi/t/proposal-to-add-fusdc-fdai-to-the-curve-gauge-controller/9098)

Articles, posts, tweets and other useful content:

* [The Defiant article](https://thedefiant.io/flux-lending-tokenized-treasuries)
* [Short Term Government Bond ETF List](https://etfdb.com/themes/short-term-government-bond-etfs/)
* [Crypto Economy post](https://crypto-economy.com/defi-platform-flux-finance-rolls-out-lending-token-collateralized-by-u-s-treasury-debt/)
* [iShares Short Treasury Bond ETF](https://www.ishares.com/us/literature/fact-sheet/shv-ishares-short-treasury-bond-etf-fund-fact-sheet-en-us.pdf) - Fact Sheet
* [Twitter thread - why Bond ETF and not directly exposure](https://twitter.com/nathanlallman/status/1640773058825953280)

Adresses

* [Flux OUSG (fOUSG)](https://etherscan.io/token/0x1dD7950c266fB1be96180a8FDb0591F70200E018#code)
* [OUSG](https://etherscan.io/token/0x1B19C19393e2d034D8Ff31ff34c81252FcBbee92)
* [Timelock](https://etherscan.io/address/0x2c5898da4df1d45eab2b7b192a361c3b9eb18d9c#readContract)
* [ONDO token](https://www.contractreader.io/contract/mainnet/0xfAbA6f8e4a5E8Ab82F62fe7C39859FA577269BE3)
* [Ondo Finance Cash Manager](https://etherscan.io/address/0x3501883a646f1F8417BcB62162372550954D618f#code)
* [Coinbase Prime address](https://etherscan.io/address/0xF67416a2C49f6A46FEe1c47681C5a3832cf8856c)
* [Management multisig](https://etherscan.io/address/0xAEd4caF2E535D964165B4392342F71bac77e8367#code)
* [OUSG redemption multi-sig](https://etherscan.io/address/0x72Be8C14B7564f7a61ba2f6B7E50D18DC1D4B63D)
* [KYC Registry](https://etherscan.io/address/0x7cE91291846502D50D635163135B2d40a602dc70#code)


## TLDR

Flux Finance has [proposed adding the fUSDC-fDAI pool](https://gov.curve.fi/t/proposal-to-add-fusdc-fdai-to-the-curve-gauge-controller/9098) to the Curve Gauge Controller, allowing users to assign gauge weight and mint CRV. This proposal aims to enhance liquidity and scale usage of the pool, which enables fDAI or fUSDC holders to benefit from additional instant liquidity through swapping and is currently in the discussion phase in [Curve forum](https://gov.curve.fi/t/proposal-to-add-fusdc-fdai-to-the-curve-gauge-controller/9098). Flux Finance currently does not have any active pools within Curve. Flux Finance will incentivize the pool to attract liquidity providers. Flux is a special-purpose lending protocol facilitating stablecoin loans against tokenized US Treasuries collateral, developed by Ondo and now owned by Flux Finance. The protocol is governed by the Ondo DAO, with discussions taking place on the governance forum and votes held on Tally.

[Ondo Finance](https://ondo.finance/) is a DeFi platform offering various financial services, including tokenized securities (OUSG). Its flagship product, [OUSG](https://ondo.finance/ousg), is a tokenized security backed by the [SHV ETF](https://www.ishares.com/us/products/239466/ishares-short-treasury-bond-etf), providing users exposure to short-duration US Treasury securities.[ Flux Finance](https://fluxfinance.com/), a lending protocol, is designed to complement Ondo's products by offering flexible lending services. LlamaRisk conducted an extensive risk analysis on Ondo Finance and Flux Finance, revealing several risk vectors:



1. Smart Contract Risk: Ondo's smart contracts underwent an audit by C4A, identifying one high-severity vulnerability, five medium-severity vulnerabilities, and numerous low-severity and non-critical issues. The Ondo team worked with C4A to resolve these vulnerabilities, particularly the high-risk related to "Loss of user funds when completing CASH redemptions".
2. Governance Risk: Ondo employs a two-stage governance process to ensure community involvement and reduce potential risks. Despite this, voting power distribution appears highly centralized, with two governors, "Glass markets" and "vexmachina.eth," holding a significant share of voting power. A treasury multi-sig arrangement controls 88% of the ONDO token total supply, raising concerns about centralized decision-making.
3. Centralization Risk: Ondo Finance relies on centralized exchanges like Coinbase and third-party service providers like NAV Consulting. Many of its products are held in third-party ETFs such as the Blackrock's iShares Short Treasury Bond ETF. This reliance could expose the platform to additional risks associated with centralized institutions.
4. Collateral/Solvency Risk: Flux Finance faces potential risks during extreme market volatility, even though it primarily supports stablecoins. The liquidation process ensures compliance with underlying asset permissions but may be slowed down, increasing the risk of bad debt accrual. Additionally, relying on third-party liquidators might not guarantee timely liquidations.
5. Oracle Risk: Ondo Finance uses NAV Consulting for daily price feeds and its custom price oracle, OndoPriceOraclev2, for managing markets. However, third-party oracle providers introduce potential risks to the protocol as there is no on-chain feed for the price of its assets.

LlamaRisk Gauge Criteria assessed the centralization, economic, and security factors of Ondo Finance, highlighting possible exploitation risks by single entities and the project's dependence on the current team. The OUSG token's backing by the SHV ETF ensures redemptions even during sudden surges, and proactive measures taken by the Ondo team make it a suitable addition to the curve gauge.


## Introduction to Ondo Finance

Ondo Finance is a decentralized platform that provides various DeFi services, such as designing, creating, and managing investment fund products. The platform aims to bridge the gap between traditional finance (TradFi) and decentralized finance (DeFi) by onboarding real-world assets (RWAs) in the form of tokenized securities.

Additionally, Ondo Finance seeks to develop decentralized, composable protocols and offer tailored services catering to organizations, DAOs, and high-net-worth individuals. A comprehensive understanding of the platform's approach, its ability to serve a diverse range of stakeholders, and the challenges that may arise is essential when evaluating its overall impact on the DeFi ecosystem.

The OUSG token, a tokenized fund that invests in short-term US Treasuries, is one of Ondo Finance's key offerings. A careful examination of this innovative approach to incorporating real-world assets into DeFi is crucial for understanding the associated challenges and potential implications for the broader decentralized finance ecosystem.

Ondo Finance operates with a standard fund structure that includes a limited and general partner, as well as third-party service providers such as qualified custodians, a fund administrator, and a financial auditor. In this section, we provide an overview of the main parties involved and outline the subscription and redemption process for Ondo I LP.

In terms of off-chain protection, OUSG holders have [SIPC coverage](https://www.sipc.org/for-investors/what-sipc-protects) that is capped at $500k, as Ondo Finance has an account with Clear Street, a brokerage firm that is a [member of SIPC](https://clearstreet.io/regulatory). However, the amount covered by SIPC is irrelevant if we compare it with the value of the Ondo I LP fund assets. Worth mentioning that account on the “Ondo I LP” name is a “cash account” (not a “margin account”), so Clear Street can't use account securities for rehypothecation.

Investment Workflow:

The following workflows outline the subscription and redemption process for investors contributing stablecoins, although fiat is also supported.

Subscription (issuance) Process:

1. Complete KYC/AML process with Ondo by providing the required documents and passing automated screenings.
2. Review and sign fund documents.
3. Provide an Ethereum wallet address for whitelisting to make subscriptions, receive fund tokens, and perform redemptions.
4. Send USDC to the fund's smart contract for subscription.
5. The smart contract logs your subscription request and atomically (immediately) transfers the USDC to the fund’s account at Coinbase Custody.
6. After computing the next daily NAV and accepting your subscription request, you'll receive OUSG tokens representing your shares in the fund.
7. Ondo IM uses the USD at Clear Street to purchase the ETF.
8. ETF dividends are reinvested by purchasing more ETF shares, increasing the fund's value.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/57aa676f-5bd9-4d28-8031-0173fc66c32a)

(Subscription Process)

Redemption Process:

1. Submit a redemption request by sending OUSG tokens to the Cash Manager’s smart contract.
2. The smart contract logs your redemption request.
3. Once the next daily NAV is computed and your redemption request is accepted, Ondo IM sells sufficient ETF shares to cover your redemption.
4. Clear Street will wire the resulting USD to Coinbase, who will convert it to USDC.
5. Ondo IM will complete the redemption request and distribute the USDC to the user's wallet.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/f5e56545-8d54-43d4-a323-6a4c51bce448)

(Redemption process)

Key Parties Involved:

* Ondo I GP: The General Partner (GP) who manages the fund and instructs service providers.
* Ondo Capital Management: The Investment Manager (Ondo IM) who collaborates with the GP to manage the fund.
* Ondo Finance Inc.: The technology services company assisting with fund tokenization.
* Ondo I LP: The Delaware limited partnership holding the fund assets and receiving investor capital contributions.
* OUSG, OSTB, OHYG: Tokens representing various share classes ownership in the fund, each with a separate strategy and assets in distinct sub-accounts at the custodians.
* Qualified Custodians: Regulator-approved institutions holding client assets in separate accounts under the client's name.
* Clear Street: The securities brokerage and qualified custodian managing off-chain assets and trade orders for the fund.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/20bb04e4-58c7-40f6-bf98-caec2051f2b8)

(source: [MakerDAO Governance Forum](https://forum.makerdao.com/t/mip119-onboard-dai-funds-to-the-flux-finance-dai-lending-pool/19885/9))

Ondo Finance implements extensive security measures to ensure the safe and efficient management of funds, collaborating with reputable service providers like Coinbase and Clear Street. The Fund has established access controls to ensure security, especially for third-party transfers. Accounts at Coinbase are only permitted to send US dollar wire transfers to the Fund's account at Clear Street. The Clear Street account wires are sent and received through its bank, BMO Harris, while Coinbase wires are sent and received through its bank, Silvergate Bank. To approve another account for wire transfers, the Fund must first receive a wire transfer from that bank account to the Fund's Coinbase account and then work with a Coinbase representative to configure the bank as a trusted withdrawal destination. Additionally, Ondo maintains criteria for approving new bank accounts as transfer destinations.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/0fbb9b64-ba56-4d31-b772-5c4a4e49508a)

(source:[NAV Consulting](https://www.dropbox.com/sh/m6s7l9tiex7hex1/AACiqtviGv274DiEHiJGMO8va?dl=0))

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/b5fb0e31-f05b-43e0-9f45-1f4134b0f5bc)

(source:[NAV Consulting](https://www.dropbox.com/sh/m6s7l9tiex7hex1/AACiqtviGv274DiEHiJGMO8va?dl=0))

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/84760d55-5c04-4702-b4b6-acd50c50f804)

(source:[NAV Consulting](https://www.dropbox.com/sh/m6s7l9tiex7hex1/AACiqtviGv274DiEHiJGMO8va?dl=0))

The Llama risk team has examined Ondo Finance's documentation, including the trial balance, account statement, and balance sheet, comparing them to the on-chain data. It was noted that there are no material differences between NAV Consulting reporting and on-chain data.


## Introduction to Flux Finance

Flux Finance, a project developed by the Ondo Finance team, is a decentralized peer-to-pool lending protocol overseen by the Ondo DAO ([ONDO token](https://www.coingecko.com/en/coins/ondo-finance) holders). As a fork of Compound V2, the protocol has various tokens available such as USDC, DAI, USDT, FRAX, and also permissioned tokens like OUSG. Flux Finance's primary goal is to support OUSG as the exclusive collateral, which cannot be borrowed against, in order to facilitate the onboarding of real-world assets onto the blockchain in a compliant manner. The figure below depicts how Ondo and Flux ecosystems interact with each other.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/9ce86712-ed9c-415a-b539-c1493bb423cb)

(source: [MakerDAO Governance Forum](https://forum.makerdao.com/t/mip119-onboard-dai-funds-to-the-flux-finance-dai-lending-pool/19885/9))

In its attempt to integrate various assets, Flux Finance aims to address the diverse requirements of each asset class. This approach to decentralized finance (DeFi) seeks to ensure that every token operates within a suitable framework, promoting an environment that balances accessibility and compliance. 


### fTokens

Users can deposit stablecoins such as USDC, DAI, USDT, and FRAX, which become available for borrowing by those who post OUSG as collateral. Flux Finance allows lenders to earn interest on their stablecoins by supplying them to the platform and minting fTokens. These ERC-20 tokens represent balances on the protocol and function similarly to Compound Finance's cTokens. At the moment OUSG Collateral Factor (CR=LTV) is set to [92%](https://fluxfinance.com/market/ousg), Close Factor to[ 50%](https://etherscan.io/address/0x95Af143a021DF745bc78e845b54591C53a8B3A51#readProxyContract) and Liquidation Premium to [5%](https://etherscan.io/address/0x95Af143a021DF745bc78e845b54591C53a8B3A51#readProxyContract).

Supply and borrow rates on Flux Finance are algorithmically determined based on supply and demand, following a model similar to Compound. The interest earned by the protocol is not directly distributed to lenders. Instead, the fToken exchange rate increases over time, allowing users to redeem more assets as interest accrues.

Notably, fTokens represent an enhanced version of Compound V2's cTokens, incorporating advanced features to accommodate permissioned assets such as OUSG. Borrowers can leverage fTokens as collateral for securing loans in other assets, while simultaneously earning interest on the collateralized fTokens. This mechanism could counterbalance a portion of the borrowing expenses.

While fTokens are generally transferable, they respect the underlying asset's transfer restrictions for permissioned assets. Transfers that would result in negative account liquidity for borrowers will fail, ensuring the stability and security of the protocol.

Addresses (Token contracts):

* Flux USDC ([fUSDC](https://etherscan.io/token/0x465a5a630482f3abD6d3b84B39B29b07214d19e5))
* Flux DAI ([fDAI](https://etherscan.io/token/0xe2bA8693cE7474900A045757fe0efCa900F6530b))
* Flux USDT ([fUSDT](https://etherscan.io/token/0x81994b9607e06ab3d5cF3AffF9a67374f05F27d7))
* Flux FRAX ([fFRAX](https://etherscan.io/token/0x1C9A2d6b33B4826757273D47ebEe0e2DddcD978B))
* Flux OUSG ([fOUSG](https://etherscan.io/token/0x1dD7950c266fB1be96180a8FDb0591F70200E018))

According to the Defi Llama and TVL calculation method that includes the borrowed amount (the Flux protocol has separate lending and borrowing parties - isolated permissions), the Flux protocol has a TVL of $57.95m of which 60% is OUSG.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/bf64d33c-2472-4e7c-be55-15387b8b87bf)


### Overview of the Flux Finance Ecosystem

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/0671dcae-d6a5-42b9-b9b0-c31d0e9914b8)

(source: [Flux finance markets](https://fluxfinance.com/markets) )

The illustration above reveals around 90% utilization rate for permissionless fTokens as an equilibrium where OUSG yield (underlying asset - SHV ETF yield) matches the borrowing cost of supported stablecoins. Given that the permissioned token OUSG is exclusively used as collateral (permissionless fTokens can only be borrowed) it can be deduced that permissionless fTokens at a 90% utilization rate signifies the maximum capacity at which OUSG lenders can borrow without experiencing losses or negative annual percentage yields (APY).

**A** - Urate 90% - Borrow APY = 4.41%

**B** - Urate 91% - Borrow APY = 4.78%

**C** - SHV ETF (underlying asset yield) - 4.65% - annual fee cost 0.15% (Ondo management fees), 0.15% max fee for fund expenses and 0.15% management fees from ETF fund (BlackRock)

**D** - Current Borrow APY for Flux stablecoins (average) - 4.575% (lowest USDC - 3.85% and highest USDT 5.6%)

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/d3f0924d-4739-4c36-9fdd-6e3ccb478829)

(source: [Ondo Finance Twitter](https://twitter.com/OndoFinance/status/1649051019756847105))

By accounting for management costs (0.45%) and reducing the underlying collateral APY accordingly, OUSG depositors currently experience a borrowing rate of 4.65%, which results in a loss or negative APY for USDT, DAI and FRAX and positive for USDC borrowers. 

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/cb8d416f-5b33-4273-a582-302879f5f099)

(source: [Flux Finance markets](https://fluxfinance.com/markets))

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/25719b47-65a5-4fe2-b5af-36366191f337)

(source: [Flux Finance markets](https://fluxfinance.com/markets))

Given the current lending protocol (and respectively fTokens) utilization rate, it is necessary to add/assign some extrinsic productivity to fTokens to fulfill the demand for using OUSG as collateral. 

Ondo Finance team already works on fTokens composability; aside from the current Curve proposal, they also made a [proposal to MakerDAO](https://forum.makerdao.com/t/mip119-onboard-dai-funds-to-the-flux-finance-dai-lending-pool/19885). MIP119 proposes to create a DAI 500MM vault for lending to the Flux Finance DAI Lending Pool, a decentralized lending protocol developed by Ondo Finance. 

At the moment, there are [33 OUSG token holders](https://etherscan.io/token/0x1b19c19393e2d034d8ff31ff34c81252fcbbee92#balances). The largest holder is Flux Finance (fOUSG) with a ~31.05% share of the total supply. Given that currently the OUSG token is capital productive only as collateral on the Flux protocol, the relationship between the fOUSG supply and total OUSG supply can serve as an indicator of how much capacity is utilized in relation to the potential (maximum) OUSG capacity.

Regarding the permissionless side of the protocol, fUSDC has [420](https://etherscan.io/token/0x465a5a630482f3abd6d3b84b39b29b07214d19e5#balances) token holders, fDAI [160](https://etherscan.io/token/0xe2bA8693cE7474900A045757fe0efCa900F6530b), fUSDT [76](https://etherscan.io/token/0x81994b9607e06ab3d5cf3afff9a67374f05f27d7), and fFRAX only [7](https://etherscan.io/token/0x1c9a2d6b33b4826757273d47ebee0e2dddcd978b) holders. Although supplying (lending) [Interest Rates are competitive](https://defillama.com/yields?token=USDC&category=Lending&category=CDP) against larger money market protocols, on-chain adoption seems quite low. 


### Flux Finance Governance

Flux Finance is governed by [Ondo DAO](https://www.tally.xyz/gov/ondo-dao), more precisely by ONDO token holders who have control over protocol economic parameters, smart contract upgrades through on-chain proposals, control OUSG oracle and lending protocol interest rate model contracts. Although the ONDO token is still non-transferable, users can use the token to vote on DAO proposals or delegate voting power to another account.

Ondo DAO governance follows a standard two-step process:

1. [Forum discussion](https://forum.fluxfinance.com/)
2. On-chain voting (managed by [Tally](https://www.tally.xyz/gov/ondo-dao))

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/5f8c30a2-e885-4156-acc7-184fd7d77329)

(source: [Flux finance docs](https://docs.fluxfinance.com/governance/ondo-dao))

The ONDO token has a max total supply set to 10,000,000,000 ONDO tokens with the following token allocation and vesting schedule:

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/96e37a19-9194-4dcd-a421-97be1aa19d91)

(source: [Vestlab](https://vestlab.io/ondo-finance))

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/a8009b8f-f359-4b92-a180-f99ad63a796c)

(source: [Etherscan](https://etherscan.io/address/0xfaba6f8e4a5e8ab82f62fe7c39859fa577269be3#readContract))

At the time of writing, the ONDO token boasts [9,770 holders](https://etherscan.io/token/0xfaba6f8e4a5e8ab82f62fe7c39859fa577269be3#balances), all of whom have completed KYC during the public and private sale events. These token distribution initiatives were facilitated through the [Coinlist platform](https://blog.coinlist.co/announcing-the-ondo-token-sale-on-coinlist/), where 11.31% of the total ONDO supply was allocated. The remaining supply, accounting for 88.69% of undistributed ONDO, is held in the[ treasury multi-signature](https://etherscan.io/address/0x677fd4ed8ae623f2f625deb2d64f2070e46ca1a1#readProxyContract) wallet.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/4915f637-4daa-4816-9ae1-f3e8bbdd14ba)

(source: [Etherscan](https://etherscan.io/token/0xfaba6f8e4a5e8ab82f62fe7c39859fa577269be3#balances))

Per the Ondo DAO governance profile on [Boardroom](https://boardroom.io/ondoDao/overview), the platform has seen six proposals since its launch, with 762 participating voters and a total of 1,589 votes cast. Examining the delegate landscape, the two largest accounts ([Account1](https://boardroom.io/voter/0x118919e891D0205A7492650AD32E727617FA9452https://boardroom.io/voter/0x118919e891D0205A7492650AD32E727617FA9452) and [Account2](https://boardroom.io/voter/0xD2e6E930E25456fFcD4Df0124563cC334F3284f4)) collectively hold approximately 70% of the DAO's total voting power. While these accounts have voting restrictions, they can create and submit new proposals.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/2f52ca0f-bba2-4f38-a464-1394397624a7)

(source: [Boardroom - Ondo DAO](https://boardroom.io/ondoDao/delegates))

The two accounts with the highest voting power possess 202,806,000 ONDO, contributing to a voting weight of approximately 70%. However, these accounts are subject to voting restrictions, leaving 30% of the weighted voting power available, which equates to roughly 86,916,850 ONDO tokens. The three delegates with a combined 65.28% share of the total weighted voting power include:

1. [glassmarkets.eth](https://boardroom.io/voter/0x78A8AE116443B61Dadb88D186A0d9d6630F61259) - ~24.063m VP(894 delegators)
2. [0xcd7979e12E2A502a280270827077Fd7f206f9a44](https://boardroom.io/voter/0xcd7979e12E2A502a280270827077Fd7f206f9a44) (inactive during previous proposals) - 20.52m VP (193 delegators)
3. [vexmachina.eth](https://boardroom.io/voter/0xF8dFC5643A1d76900E823433a2a2F486559Db62A) - 12.164m VP (33 delegators)

The voting restrictions for the two above-mentioned accounts are set by the admins in the settings on the Tally page. Please note that Ondo uses role-based access control (RBAC) in its smart contracts and reserves the right to deploy additional multisigs to utilize a more secure and granular RBAC scheme.

Ondo Finance currently maintains three multi-signature wallets. Prior to the implementation of [FIP-04](https://forum.fluxfinance.com/t/fip-04-removing-trust-for-daily-rwa-price-and-yield-curve-updates/306/3), there were four wallets, but the privileges from the Neptune Foundation have since been transferred to the DAO. These wallets consist of the following:

**Flux protocol treasury [3/6 multi-sig](https://etherscan.io/address/0x677fd4ed8ae623f2f625deb2d64f2070e46ca1a1#readProxyContract)** holds over 88.7% of ONDO token supply

**Neptune Foundation (fluxfinance.eth) [3/6 multi-sig](https://etherscan.io/address/0x118919e891d0205a7492650ad32e727617fa9452#code)** - control Flux protocol Interest Rate Model and Oracle contracts, but voting on governance proposal [FIP-04](https://forum.fluxfinance.com/t/fip-04-removing-trust-for-daily-rwa-price-and-yield-curve-updates/306/3) is in progress and if proposal passed, ownership of these contracts will be transferred to the DAO.

**Ondo Cash Management [multi-sig 3/6](https://etherscan.io/address/0xAEd4caF2E535D964165B4392342F71bac77e8367)** has following capabilities (source: [MakerDAO forum](https://forum.makerdao.com/t/mip119-onboard-dai-funds-to-the-flux-finance-dai-lending-pool/19885)):

* Configure minimum redemption and subscription amounts on the CashManager contract.
* Configure rate limiter parameters on the CashManager contract. (i.e. what quantity of subscriptions and redemptions can be serviced in a single day)
* Configure fee recipients on the CashManager contract (fees are currently turned off).
* Set exchange rates for the minting of OUSG.
* Mint OUSG to service subscriptions.
* Pause functionality on the CashManager contract in the event of an emergency
* Burn OUSG in the event of an emergency.
* Upgrade the OUSG implementation contract in the event of an emergency.
* Execute a multicall function in the CashManager contract for the scenario in which a user accidentally transfers tokens to the CashManager contract.

**Ondo Redemption [multi-sig 3/7](https://etherscan.io/address/0x72Be8C14B7564f7a61ba2f6B7E50D18DC1D4B63D#readProxyContract)** can send stablecoins received by [Coinbase Prime custody wallet](https://etherscan.io/address/0xF67416a2C49f6A46FEe1c47681C5a3832cf8856c) to Cash Manager contract to service redemption.

It is evident that the Ondo Finance team has control over all decisions related to the Flux protocol. Although it is stated on the Tally page that the two accounts with the highest voting power are non-voting accounts, the same is not implemented (restricted) in Governor smart contract. In this case, "non-voting" accounts can be included in the voting process at any time.


## Risk Vectors

### Smart Contract Risk

Ondo Finance's smart contracts have undergone an audit performed by C4A, which assessed the security and potential vulnerabilities of the code. The audit evaluated 19 smart contracts, five abstracts, and six interfaces, totaling 4,365 lines of Solidity code.

The Ondo team has worked alongside C4A to resolve any critical vulnerabilities in the smart contracts. The C4A auditors identified six unique vulnerabilities, with one classified as high severity and five as medium severity. Additionally, the audit included 54 reports detailing low-severity or non-critical issues and 24 reports recommending gas optimizations.

The key high-risk finding, titled "Loss of user funds when completing cash redemptions" concerns the completeRedemptions function in the CashManager contract. The issue arises from the total refunded amount not being updated in the _totalBurned_ storage variable for the given epoch. If the manager completes refunds and redemptions at different steps or stages for a given epoch, using multiple calls to the_ completeRedemptions_ function, any refunded amount will not be considered in subsequent calls to the function. This discrepancy could lead to users receiving fewer collateral tokens than expected, even if they redeemed the same amount of CASH tokens, resulting in a loss of funds for the users. The Ondo team worked with C4A to [resolve](https://github.com/code-423n4/2023-01-ondo-findings/issues/325#issuecomment-https://github.com/code-423n4/2023-01-ondo-findings/issues/325#issuecomment-1410627920https://github.com/code-423n4/2023-01-ondo-findings/issues/325#issuecomment-14106279201410627920) this vulnerability. 

Among the medium-severity findings, it is important to highlight the "[First Deposit Bug](https://akshaysrivastav.hashnode.dev/first-deposit-bug-in-compoundv2-and-its-forks)" vulnerability identified in Compound v2 smart contracts. This vulnerability enables exploiters to misappropriate funds from initial depositors of newly deployed cToken contracts. The Ondo team addressed this issue by enforcing a minimum deposit that cannot be withdrawn by minting a small number of cToken units to the 0x00 (dead) address during the first deposit.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/c96d9b1b-091d-45cb-8f36-a3550151be45)

Flux Finance maintains an active [bug bounty program](https://immunefi.com/bounty/fluxfinance/) for its protocol smart contracts, hosted on ImmuneFi. The program offers a reward payout range between $1,000 and $550,000 USD, divided into four categories based on the severity or impact level of the discovered vulnerabilities:

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/855d9c4d-226c-4e40-822e-07d81dd0a55b)

Source: [ImmuneFi](https://immunefi.com/bounty/fluxfinance/)

Ondo Finance already paid one bug bounty reward of $25,000 for identifying a [high-risk vulnerability](https://iosiro.com/blog/high-risk-vulnerability-disclosed-to-ondo-finance) to security researcher [Ashiq Amien](https://ashiq.co.za/) on 26 January 2022. That issue was related to the [TrancheToken smart contract](https://etherscan.io/address/0xb279d1ed3848cee8ba6dba426be620a289ccef10#readContract), part of the first Ondo Finance product - [Ondo Vaults](https://v1.ondo.finance/). It was structured finance protocol on Ethereum, built on top of Uniswap.


### Governance Risk

Flux Finance employs a two-stage governance process involving a forum discussion and an on-chain vote to ensure community involvement and reduce potential risks. Governance proposals are typically initiated with a post on the [Flux Finance Governance Forum](https://forum.fluxfinance.com/), where community members and the team can provide feedback. Although not mandatory, this step increases the likelihood of a well-aligned and successful proposal.

A finalized proposal is submitted for a binding on-chain vote after the forum discussion. Flux Finance's DAO, a fork of Compound's Governor Bravo, manages on-chain voting through Tally. Voting power is determined by ONDO token ownership, and holders can delegate their voting power to other wallets.

Key DAO parameters include:

* Proposal Threshold: A minimum of 100,000,000 ONDO in voting power is required to submit a proposal, which helps to prevent spam or malicious proposals.
* Voting Period: A 3-day window during which community members can cast their votes.
* Quorum: Proposals require at least 1,000,000 ONDO in voting power to pass.
* Timelock: A 1-day delay period between the end of the voting period and the execution of successful proposals.
* This governance structure ensures community engagement, minimizes risks, and promotes transparency in Flux Finance's decision-making process.

Upon examining Ondo DAO's voting power distribution on Tally, we observe that the governance appears to be highly centralized. The two governors, "[glassmarkets.eth](https://etherscan.io/address/0x78A8AE116443B61Dadb88D186A0d9d6630F61259)" and "[vexmachina.eth](https://etherscan.io/name-lookup-search?id=vexmachina.eth)," collectively hold approximately 34.91 million ONDO tokens (including delegated tokens). In comparison to the [proposal with the highest participation rate](https://www.tally.xyz/gov/ondo-dao/proposal/3), these two accounts collectively hold a substantial share of voting power, amounting to approximately 73.57%.

Additionally, it is worth noting that the distribution of voting power within the platform is relatively concentrated. Specifically, three wallets hold a combined 65.28% of the total voting power (eligible to vote at this moment). This concentration of influence may raise concerns regarding the platform's governance and decentralization, emphasizing the need for a more balanced distribution of voting power among participants.

This centralization of voting power raises concerns about these entities' influence over the decision-making process within Ondo DAO's governance. Especially entities such as GlassMarkets, where they only own 57 Ondo but have 894 delegated, making them one of the largest voters in the DAO.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/1c037af3-d6e2-4f82-ac09-31e4d3cb4e1d)

Source: [Tally - Ondo DAO profile](https://www.tally.xyz/gov/ondo-dao/proposals)


### Centralization Risk

When assessing centralization risks, it's crucial to consider the underlying assets and infrastructure supporting the Ondo Finance ecosystem. OUSG is not directly backed by US Treasuries but by the SHV ETF, which tracks the ICE Short US Treasury Security Index. SHV is the[ iShares Short Treasury Bond ETF](https://www.ishares.com/us/products/239466/ishares-short-treasury-bond-etf) managed by Blackrock, with approximately $23 billion in assets and a 30-day average trading volume of $2,817,732.

Another aspect of centralization risk within the Ondo Finance platform is its reliance on centralized exchanges like Coinbase and Clear Street brokerage platform. This dependency on centralized service providers could expose the platform to additional risks from these institutions.

To address concerns about token backing and transparency, Ondo Finance leverages third-party service providers like NAV Consulting, a fund administration firm responsible for validating the fund's assets directly from its bank and custody accounts. Additionally, the fund undergoes an independent year-end audit by Richey May. While Ondo Finance manages the tokenization through its smart contracts, the fund administrator is responsible for maintaining off-chain records and providing monthly reports to investors. This process ensures that the token records and off-chain records are reconciled daily.


### Collateral Risk/Solvency Risk

Solvency and collateral risks associated with Flux Finance highlight potential concerns about bad debt accrual during extreme market volatility. While the platform has taken steps to minimize these risks, it is crucial to remain mindful of its limitations and vulnerabilities.

Flux Finance primarily supports stablecoins, which are less volatile by nature, reducing the risk of drastic price fluctuations. However, stablecoins are not entirely risk-free, as they may be backed by centralized entities or collateralized by other cryptocurrencies, exposing them to potential price fluctuations or regulatory actions.

In Flux Finance, liquidations are designed to be rare, since currently it only supports stablecoin markets, which are typically not very volatile. Nevertheless, in extreme scenarios where a borrower's equity becomes too low, some of its collateral may be sold off to pay back the debt. Third-party liquidators, are incentivized to assume this role by purchasing the collateral at a small discount compared to the oracle price.

Liquidations on Flux are similar to those on Compound V2, with accounts becoming subject to liquidation when their liquidity turns negative. At that point, a third-party liquidator can pay off some of the borrower's debt and seize the corresponding collateral at a discount. Unlike Compound, however, Flux liquidations respect the underlying asset's permissions, such as KYC requirements. For instance, to liquidate an account using OUSG as collateral, the liquidator must be KYC'd and whitelisted to hold that token.

In scenarios of extreme volatility, an account's equity might become negative when the LTV increases too quickly before it can be liquidated, causing the protocol and its lenders to accrue bad debt. Flux Finance's assets are generally very stable, making bad debt accrual extremely unlikely. As an additional safety mechanism, Flux's stablecoin oracles never price stablecoins above 1 USDC, reducing the risk of external oracle manipulation.

In the unlikely event of bad debt accrual, Flux's reserves in that market are first used to cover the losses. If there aren't enough reserves, some lenders may not be able to withdraw their assets.


### Oracle Risk

The protocol for tokenized securities employs [NAV Consulting](https://www.navconsulting.net/) services to provide a daily updated price feed mechanism, ensuring accurate valuation of the underlying collateral. This is only a temporary [solution](https://docs.ondo.finance/faq#is-there-an-observable-token-price), as the Ondo team is working on an on-chain oracle to provide live price updates.

NAV Consulting has limited API access to the Fund's accounts at Coinbase and Clear Street, which only allows them to view data without the ability to make any changes. On daily basis, NAV Consulting uses a specific method to compute the Net Asset Value (NAV) per Token, and can be described in this way (three steps):

* sum the present worth of all the fund assets (SHV shares, cash, and stablecoins)
* then subtracting fund’s accrued expenses and management fees 
* result is then divided by the total number of Tokens 

Using NAV Consulting calculation, Ondo updates the contract price on daily basis.

On Flux protocol, Ondo employs its custom price oracle, [OndoPriceOraclev2](https://etherscan.io/address/0x50ce56a3239671ab62f185704caedf626352741e#readContract), for managing markets. This contract enables the setting of the underlying asset price directly within the contract storage, which is currently the method Flux oracle utilizes for all fTokens across Flux lending markets. Additionally, the contract offers options to configure Compound or Chainlink oracles and establish a price cap for the underlying assets of fTokens.

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/efdf1412-f2fa-4dca-a198-8abb26514477)

Source: [Etherscan](https://etherscan.io/address/0x50ce56a3239671ab62f185704caedf626352741e#readContract)

![image](https://github.com/vefunder/protocol-research-review/assets/51072084/957b41e2-a69e-46e7-ab56-bcc5a2975cac)

Source: [GitHub](https://github.com/flux-finance/contracts/blob/main/contracts/lending/OndoPriceOracleV2.sol)

Flux Finance has introduced a [governance proposal](https://www.tally.xyz/gov/ondo-dao/proposal/7) to increase transparency in price feeds and reduce the protocol's dependence on Ondo DAO. One of the proposal's key components is the deployment of a new oracle under the control of Ondo DAO. This oracle will serve as the Flux Finance protocol's primary mechanism to retrieve underlying asset prices. The proposal also suggests the implementation of new smart contracts that limit daily price fluctuations of OUSG to 100 basis points, effectively mitigating risks associated with price volatility.


## Llama Risk Gauge Criteria

Centralization Factors

**1. Is it possible for a single entity to rug its users?**

While it is possible for a single entity to exploit the protocol, several safeguards are in place to minimize this risk. Ondo Finance employs three multi-signature wallets (Ondo management multi-sig, OUSG redemption multi-sig, and ONDO token holder multi-sig), each with a minimum execution threshold of three signatures. The same three addresses are signers for each wallet:

1. 0x3c6Fdc07A3280B79F82610525bCA7DcEb9D2F7F4
2. 0x8cc5e5E8E2EA561DB672F8eb1191336bd5C11bc7
3. 0x9019295cA2dCdC4BCFf323b562e87FC922e34C32

Although this setup theoretically allows for the coordination of the three multi-signature signers to exploit the system, the requirement of multiple signatories adds an additional layer of security. This structure helps to mitigate the risk of a single entity compromising the protocol and ensures that decision-making power is distributed among multiple parties.

**2. If the team vanishes, can the project continue?**

The reliance on third-party service providers and the use of smart contracts might enable the project to continue in the short term. However, long-term maintenance and development would likely be affected and it would be difficult to continue operations without the current team being present. Furthermore, in the event of the team vanishing the redemptions of Ondo Finance assets will be impacted causing major issues to its stakeholders.

Economic Factors

**1. Does the project's viability depend on additional incentives?**

Ondo Finance does not depend on additional incentives for its continued viability. The project has been developed with an emphasis on its essential financial services, which indicates that its sustainability is not reliant on external incentives. However, it is essential to monitor any future developments or changes in the project's structure that could affect its risk profile is essential.

**2. If demand falls to 0 tomorrow, can all users be made whole?**

If demand falls to zero tomorrow, the OUSG token's backing by the SHV ETF aims to provide a foundation for redemptions. In such an event, the SHV ETF backing is designed to ensure that Ondo Finance has the capacity to continue honoring redemption requests, making all users whole and offering a level of financial security and reassurance. However, it is crucial to understand that market risk and interest rate risk still persist.

Usual fixed income risks remain present, with interest-rate and credit risks being among the primary concerns. Generally, as interest rates increase, there is a tendency for bond values to decrease. Credit risk pertains to the possibility that the bond issuer may not fulfill their obligations concerning principal and interest payments. It is essential for investors to understand that investments in the fund are not insured or guaranteed by the Federal Deposit Insurance Corporation or any other government agency. It is important to note that the following risks are associated with the US Treasury market in general and not with Blackrock/Ondo.

Security Factors

**1. Do audits reveal any concerning signs?**

The audit conducted by C4A on Ondo Finance's smart contracts did reveal several vulnerabilities, including one high-severity issue and five medium-severity issues. One of the medium-severity issues identified is the "First Deposit Bug," which could potentially be exploited to steal funds from initial depositors of a freshly deployed CToken contract. The bug involves the manipulation of the exchange rate due to a dependency on the ratio of CToken's total supply and the underlying token balance of the CToken contract. An attacker could exploit this vulnerability by following specific steps to redeem their entire CToken balance for the contract's underlying token balance.

However, it is important to note that the Ondo team has worked closely with C4A to address and resolve any critical vulnerabilities in the smart contracts. The key high-risk finding, titled "Loss of user funds when completing CASH redemptions," has been resolved in collaboration with the auditing team.

While the presence of vulnerabilities is a concern, the proactive approach taken by the Ondo team to rectify these issues demonstrates their commitment to ensuring the security and stability of the platform.


## Risk Team Recommendation

Upon evaluating Ondo Finance and Flux Protocol, we recognize that there are areas where improvements can be made to enhance the platform's security, decentralization, and transparency. As Ondo Finance progresses, we advise the Curve DAO and community members to closely monitor its development. 

1. Address the centralization of governance and voting power in Ondo DAO. Implementing mechanisms to reduce the concentration of voting power can help promote a more decentralized and democratic governance system. It is crucial to ensure that decision-making processes are more inclusive and that influence is distributed among a larger group of participants.
2. Improve the security and stability of Ondo Finance by addressing potential risks in the smart contracts, oracles, and collateral. Regular audits and updates to the platform's security features will contribute to a more robust and reliable ecosystem. It is essential to ensure all identified vulnerabilities are resolved and measures are in place to prevent future issues.
3. Enhance the transparency of Ondo Finance's operations by providing more detailed documentation on the platform's functionality, risks, and mitigation strategies. This will allow users to make informed decisions about participating in the platform and contribute to a better understanding of the project's goals and potential risks.

We recommend that Curve treats the current gauge as a starting point for assessing Ondo Finance's risk profile, while closely monitoring the project's progress in decentralization, platform security improvements, and transparency enhancements. The project's long-term success and the sustainability of the gauge will be determined by its ability to address these critical aspects effectively.
