# Akashnet - Software Upgrade proposal:
## Foreword
In the last Akashnet upgrade, the new Akash DeCloud was released into production. We’re grateful to all those in our community who made this a reality. The upgrade included all of the advanced features from the latest Cosmos-SDK release (Stargate). \
Stargate is one of the biggest upgrades in Cosmos's history. As expected with such a significant release, we discovered a few kinks in the software.
After running in production on multiple chains, the below issues were discovered, and we are submitting this Software Upgrade Proposal to address them with this update:
1. Module accounts should not allow tokens to be transferred to them.
2. A number of vesting accounts from Genesis were not able to perform delegation operations.
None of these issues have affected account balances or consensus, nor have they allowed for double spending. The issues have not impacted Akash-specific modules and functionality in any way.
If this software upgrade proposal passes, we will have a battle-tested Stargate-based chain as a strong foundation for expanding Akash DeCloud usage and development.
## Action Plan
This Software Upgrade Proposal is for soft-upgrading the network to fix vesting accounts that were affected by the bug, and ensures future delegations can execute. On passage of the proposal, validators will need to run new software after the specified upgrade height.\
Following are the details of the upgrade:
- Software Upgrade Name: `akashnet-2-upgrade-1`
- Title: `Akashnet - Software Upgrade proposal`
- Version to use for the upgrade: `v0.12.0`
- Upgrade Height: `415200`
