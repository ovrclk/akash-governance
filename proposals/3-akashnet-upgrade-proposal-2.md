# Akash Network - Mainnet Upgrade Proposal - 2

The previous proposal to check the Akash community readiness for the mainnet upgrade is PASSED. This proposal is for completing the upgrade.

## The Upgrade Details
We'll upgrade the network to `akashnet-2` with following version:
Akash Version: `v0.10.0`
Commit Hash: `af43b89e47e50bfeedcc35c7ee77229bd258ed0d`

Note: In case of any emergency/security fixes before the upgrade time, we might want to use a minor version on from the release `v0.10.x`. All the communication and coordination will happen on #mainnet-validators channel on the Akash Discord server

We propose scheduling the upgrade for Monday Mar 08, 2021 at 1500 UTC

## The git commit and version of Akash that we are upgrading to

Akash Version: `v0.10.0`
Commit Hash: `af43b89e47e50bfeedcc35c7ee77229bd258ed0d`

## What's the testnet plan?

We expect to coordinate with exchanges, wallets, explorers and other clients & partners to finish testing their integrations with the currently running testnet (mainnet candidate).

A testnet with the final version of Akash is up and running to assist with integrations.

## Abort/Cancellation of the upgrade process

There could be some problems at the time of upgrade and the upgrade process should be abandoned even if it passes:

1. Though we have tested the software & the upgrade path multiple times, there could be unexpected issues. A critical vulnerability may be found in the software. If the development team change their recommended version of Akash and the validator set  decides to implicitly abandon this upgrade procedure, a future proposal will be made to upgrade to the new target commit. If the validator set agrees to change the version `on-the-go` via social consensus, we don't abort the upgrade process. All this communication will happen on `mainnet-validators` channel on discord. If it is at the time of upgrade process, if the fix is not available in lesser than 2 hours, we'll abort the upgrade process and restart `akashnet-1`.

2. The migration process fails could fail to produce a valid `akashnet-2` genesis file. This would manifest as ad-hoc changes to genesis needed to start or a failure to produce blocks from `akashnet-2`. In this case, the validator set should restart `akashnet-1` and a future governance proposal will be done to initiate another upgrade.
