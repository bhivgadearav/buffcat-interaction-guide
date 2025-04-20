# BuffCat Contract Interaction Guide

This guide provides instructions on how to interact with the BuffCat contract. Below are the available external functions that users can call.

# Note - User will be interacting with each lock seperately so in the UI, allow the user to swtich between and whatever locking/unlocking/rewards dashboard is present will be the same but the data like lockId etc will change.

## User Functions

### Lock Assets
Lock your tokens to earn rewards.

**Function:** `lockAssets`
**Inputs:**
- `_token` (address): Address of the token you want to lock
- `_amount` (uint256): Amount of tokens to lock
- `_lockDuration` (uint256): Duration in days
- `_lockType` (LockType): FLEXIBLE (0) or FIXED (1)
- `_referrer` (address): Referrer address (use zero address if none)

### Unlock Assets
Unlock your locked tokens.

**Function:** `unlockAssets`
**Inputs:**
- `_lockId` (uint256): ID of your lock
- `_amount` (uint256): Amount to unlock

### Claim Rewards
Claim rewards for your locked tokens.

**Function:** `claimRewards`
**Inputs:**
- `_token` (address): Token address to claim rewards in
- `_lockId` (uint256): ID of the lock to claim rewards for

### Claim Redistribution
Claim redistribution rewards for your lock. Also claim remaining redistribution rewards after unlocking 97% or more of your tokens within 1 day.

**Function:** `claimRedistribution`
**Inputs:**
- `_token` (address): Token address to claim redistribution in
- `_lockId` (uint256): ID of the lock to claim redistribution for

## Important Notes

1. Before interacting with token-related functions, ensure you have:
   - Approved the contract to spend your tokens
   - Sufficient token balance
   - Valid token and price feed addresses

2. For locking assets:
   - Minimum lock duration: 1 day
   - Maximum lock duration: 3000 days
   - Lock types: FLEXIBLE (0) or FIXED (1)

3. For claiming rewards:
   - Must wait 24 hours after creating lock
   - Must wait 24 hours between claims
   - Rewards are subject to daily limits and pool availability

4. For unlocking assets:
   - FLEXIBLE locks can be unlocked anytime
   - FIXED locks can only be unlocked after lock period ends
   - Unlocking is subject to fees

5. Error Handling:
   - All functions may revert with appropriate error messages if conditions are not met
   - Check return values where applicable to ensure successful execution 
