# cdex_rewards.sol

## CDEXStakingPool
This smart contract controls rewards deposits and withdrawals according to the amount of time that users leave CDEX tokens within the contract balance (staking).

A loyalty bonus is added to the withdrawn rewards according to the user staked balance. There are three bonus tiers which can be configured within the contract.

**The normal contract workflow happens as below:**

1. The contract owner configures the total duration for the rewarding period, in seconds, by running the function ***setRewardsDuration***.
2. The contract owner configures the loyalty tiers and the bonus percentage for each tier, through the functions ***setLoyaltyTiers*** and ***setLoyaltyTiersBonus***, respectively.
3. The contract owner deposits a reward amount with the function ***depositTokens***. That amount needs to consider an extra percentage to be dedicated to the loyalty bonus funds. For example, if the total percentage for the three loyalty bonus layers is 3% and the user wants a reward of 100,000 CODEX, they owner has to deposit 103,093 CODEX, as 3,093 CODEX will be distributed as loyalty bonus on top of the 100,000 CODEX.
4. The contract owner enables the reward with the function ***notifyRewardAmount***. That function will enable the staking and the rewarding period starts counting.
5. The users start staking by running the function ***stake***. That function will transfer CDEX tokens into the smart contract balance.
6. The users withdraw their **rewards** by running the function ***getReward***. The function calls ***earned***, which calculates the owed rewards based on the amount of seconds elapsed between the user staking and the moment of the function execution. The ***rewardPerToken*** function is also leveraged to capture how much to pay per staked token.
Any extra loytaly bonus are added in the reward calculation and added to the final withdraw amount.
5. The users can also unstake their CDEX tokens from the contract by running the function ***withdraw***.

### Methods

#### balanceOf(address)


|Parameter|Description|
|---------|-----------|
|account|The address owning the balance|

#### depositTokens(uint256)


|Parameter|Description|
|---------|-----------|
|amount|The value of tokens to be added to the balance.        To make it easier for the contract owner, the expected amount        is in the integer format (without the 8 zeroes).|

#### earned(address)


|Parameter|Description|
|---------|-----------|
|account|The address owning the accrued reward.|

#### getLoyaltyTiers()

#### getLoyaltyTiersBonus()

#### getRewardForDuration()

#### lastTimeRewardApplicable()

#### min(uint256,uint256)


|Parameter|Description|
|---------|-----------|
|a|The first value to be compared|
|b|The second value to be compared|

#### notifyRewardAmount(uint256)


|Parameter|Description|
|---------|-----------|
|reward|The amount to be distributed between the stakers.        To make it easier for the contract owner, the expected amount        is in the integer format (without the 8 zeroes).|

#### rewardPerToken()

#### setLoyaltyTiers(uint256,uint256,uint256)


|Parameter|Description|
|---------|-----------|
|_loyaltyTier1|The minimum staked amount to be in Tier 1|
|_loyaltyTier2|The minimum staked amount to be in Tier 2|
|_loyaltyTier3|The minimum staked amount to be in Tier 3|

#### setLoyaltyTiersBonus(uint256,uint256,uint256)


|Parameter|Description|
|---------|-----------|
|_loyaltyTier1Bonus|The bonus percentage for Tier 1|
|_loyaltyTier2Bonus|The bonus percentage for Tier 2|
|_loyaltyTier3Bonus|The bonus percentage for Tier 3|

#### setPaused(bool)

Only the contract owner may call this.

#### setRankingContract(address)


|Parameter|Description|
|---------|-----------|
|_contractAddress|The address of the contract where        the new instance will point to|

#### setRewardsDuration(uint256)


|Parameter|Description|
|---------|-----------|
|_rewardsDuration|The duration in seconds for the staking period|

#### setTokenContract(address)


|Parameter|Description|
|---------|-----------|
|_contractAddress|The address of the contract where        the new instance will point to|

#### stake(uint256)


|Parameter|Description|
|---------|-----------|
|amount|The amount of tokens to be staked by the user.|

#### totalSupply()

#### withdraw(uint256)


|Parameter|Description|
|---------|-----------|
|amount|The amount of tokens to be withdrawn.|

## Pausable

### Methods

#### setPaused(bool)

Only the contract owner may call this.

