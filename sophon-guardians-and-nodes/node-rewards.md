# Node Rewards

20% of the $SOPH token supply is allocated as rewards for Sophon Guardians over 3 years (156 weeks) counting from the full public launch of Sophon network (expected on Q4 2024). This allocation is divided into three categories:

### All Active Delegated Memberships

* Distributed to all delegated memberships that are being used on any active nodes&#x20;
* 5% of $SOPH token total supply with a proportional distribution every week
* Each active membership receives 1/(total supply of memberships) portion of the weekly reward
* Memberships that are not active for a given week do not receive the weekly reward
* Example Calculation:
  *   Let’s say you own 1 membership. Here’s how your weekly reward is calculated:

      * The total supply of $SOPH tokens is 10 billion.
      * 5% of this supply is allocated for rewards over 3 years.
      * There are approximately 120,000 memberships in total, and the reward period lasts for 156 weeks.
      * To calculate your weekly reward: &#x20;

      $$\frac{10^{10} \times 0.05}{120,000 \times 156} ≈ 27$$ $SOPH

### Sophon Light Nodes

* 10% of the total $SOPH token supply is allocated for rewards over 3 years, with approximately 0.064% distributed per week.
* A minimum liveness threshold is required for a light node to qualify for rewards.
* Weekly rewards are fully distributed to active nodes based on their participation.
*   Example Calculation:

    * Let’s say there is an operator running a light node with 20 memberships delegated to it.&#x20;
    * The total supply of $SOPH tokens is 10 billion.
    * There are 60,000 active memberships.
    * The reward is distributed weekly over 156 weeks.
    * The weekly reward of that operator would be:

    $$\frac{10^{10} \times 0.1 \times 20}{156 \times 60,000} \approx 2,136$$ $SOPH


* The split between the operator running the light node and the delegates is defined by the former, and it is up to Guardians to accept or look for other operators.

### Sophon Full Nodes

* 5% of the total $SOPH token supply is allocated for rewards over 3 years, with approximately 0.032% distributed per week.
* Weekly rewards are fully distributed to active nodes.
*   Example Calculation:

    * Let’s say an operator has 20,000 delegated memberships.
    * The total supply of $SOPH tokens is 10 billion.
    * Weekly distribution is approximately 0.032% of the total supply.
    * There are 80,000 active delegated memberships, including yours.
    * To calculate your weekly reward:

    $$\frac{10^{10} \times 0.00032 \times 20,000}{80,000} \approx 800,000$$ $SOPH
* The split between the operator running the full node and the delegates is defined by the former, and it is up to Guardians to accept or look for other operators.

> **Important Note:** During the initial period where only Sophon Labs will be running a sequencer node, **100% of the Full node rewards** will be distributed directly to the Sophon Guardians that delegated memberships to it.

***

Rewards will be distributed at a weekly basis, with each distribution subject to a 3-month lockup period after claiming. Users have the option to unlock their rewards with immediate effect, but doing so will incur a linear penalty until the 3-month lockup period is complete. Example below:

* A Guardian claims 10 $SOPH, starting the 3-month lock up period
* After one and a half month, the Guardian decides to unlock rewards - instead of receving the 10 $SOPH, they will receive 5 $SOPH.
