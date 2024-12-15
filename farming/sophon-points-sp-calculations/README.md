# Sophon points (SP) calculations

### How SP accrues on-chain

```
SP per Block = (User’s Pool Allocation * Pool's SP Per Allocation) 
```

The amount of SP a user has is calculated by considering:

* **User's portion of the pool**: The system takes the total amount of assets the user has staked in the pool (including any [boosted](../boosts/) amounts) and calculates the percentage the user deposited in relation to the pool total.
* **Pool's SP per each user’s portion**: Within the Sophon Points framework, rewards are distributed from a shared pool that accumulates over time. Each participant's portion of this pool is determined by their proportional liquidity contribution. As the number of participating pools increases or decreases, the points allocated proportionally fluctuate. For example, if a pool initially has 100 points to distribute, and Alice deposits 60% of the total liquidity while Bob deposits 40%, Alice would receive 60 SP, and Bob would receive 40 SP. If another participant joins or someone withdraws, the points allocation will be recalculated to reflect the updated proportions. Keep an eye on the [Farming Portal](https://farm.sophon.xyz/) for details on pool distribution totals.&#x20;
* **User's rewards**: A user's rewards are calculated based on their portion of the pool and the total points the pool has earned. This is done by considering the user's proportional contribution to the pool's liquidity, including any boosted amounts, and multiplying it by the points per share the pool has accumulated.&#x20;

This final number represents the amount of SP the user can claim.

**SP calculation example:**

Let's say a user has staked 100 BEAM in a pool, and the pool's SP earned per BEAM is 50.

Using the formula, we can find total SP:

```
SP = (100 BEAM * 50 SP/BEAM) = 5000 SP
```

The user has 5000 SP.
