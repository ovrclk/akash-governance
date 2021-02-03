# Akash Network Upgrade Proposal
## Context:
With the recent incentivized testnet program, **The Akashian Challenge’ phase-3**, it's
clear that the Akash Software is ready to be used in production to make DeCloud a
reality. The software used in the incentivized testnet had some minor issues and it was
using RCs (pre releases) from Cosmos-SDK. Meanwhile Cosmos-SDK also had
many improvements and fixes. We have a final Stargate a.k.a `v0.41.0` release from
Cosmos-SDK now.

Akash team is following the SDK changes closely and updating the code base. It is time to plan the mainnet upgrade for Akash Network to experience the real power of decentralized cloud and IBC from the Stargate release of Cosmos-SDK. Akash Network would be one of the first chains to integrate IBC. The latest Stargate version of the Cosmos-SDK has a number of changes implemented and it is important to co-ordinate and allow Akash Network partners to upgrade and test their integrations. Though most of the co-ordination happened on CosmosHub testnets, it’s still important to test and verify the integrations with Akash Network. The following stakeholders will be impacted: 
- Exchanges
- Wallets
- Block Explorers
- Staking Dashboards
- Validators & Delegators (Infra, tools & scripts, ledgers etc)

The major expectation out of this proposal is to get a signal of approval from the
ecosystem players on the changes and risks with the upgrade and readiness for the
upgrade.

### The Upgrade Plan:
- Run the Akash-Stargate testnet and coordinate with other stakeholders to update
and test their integrations
- Create documentation and FAQs to help new partners
- Test the upgrade path from `akashnet-1` to `akashnet-2`
- Verify the state migrations
- Test all the transactions and queries to ensure a stable software for the upgrade
AkashNet Stargate Testnet:
Vitwit (Witval validator) will lead and execute the testnet and coordinate with all the
validators and other stakeholders.
- Plan the testnet to test the upgrade path. This should include the real testing of
state export, migration and upgrade.
- Help document the migration path for exchanges, explorers and wallets.
Coordinate and test the integrations
- Test mainnet-2 features aka deployments, providers and marketplace
- Coordinate with the dev team and marketing team for necessary fixes and
announcements.
### After the testnet:
This proposal is intended for getting a soft-signal from the validators and community
(acceptance/rejection) for the AkashNet upgrade plan. Based on the proposal status,
there will be a second governance proposal which will have all the details about the
actual upgrade and software version details. Following are a set of actionable items
after the testnet:
- Coordinate on a final date and software version for the upgrade
- Fix any and all documentation, UX and non-state breaking issues
- Wait for the final release
- Make a proposal to upgrade the network

### Upgrade Risks and Mitigation Plans:
- There are a number of state breaking changes in the new software. Here are a
list of features added/improved
- Akash DeCloud:
- Providers
- MarketPlace: Bids, Orders, and Leases
- Deployments
- Protobuf migration: Stargate version Cosmos-SDK has one of the best
encodings now. Now we have support for both Protobuf and Amino
encoding options.
- IBC: Inter Blockchain communication is the long awaited feature from
Cosmos-SDK and is now available to use in production. This allows us to
transfer tokens between different chains securely.
- Fast Sync
- CosmoVisor
- Tendermint Changes
- It is mission critical to ensure all the state migrations happen smoothly and verify
data integrity. CosmosHub conducted a number of testnets to verify and fix the
critical paths but it's very important to test these migrations thoroughly and fix
integrations with other clients.
- If something goes wrong while upgrading, we should have a rollback mechanism
defined clearly to ensure a smooth restart of the existing network and push the
upgrade until further notice. All the coordination should happen over the discord
#testnet-validators channel.
