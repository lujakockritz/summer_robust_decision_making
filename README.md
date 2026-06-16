# Scenario Discovery for Global Net-Zero CO2 by 2070

## Project aim

We use the **Scenario Compass** ensemble to understand **which pathway characteristics are associated with reaching global net-zero CO2 emissions by 2070**.

Some scenarios reach net zero by 2070.

Some do not.

Our job is not to predict the future.

Our job is to ask:

**Where do scenarios look robust?**
**Where do scenarios look vulnerable?**
**Which pathway features separate success from failure?**

## Novelty

We are not just counting how many scenarios reach net zero.

The novelty is that we turn the scenario ensemble into a **decision-relevant vulnerability map**.

Instead of saying:

> 481 scenarios succeed and the rest fail.

We ask:

> Under what pathway conditions do scenarios reach net-zero CO2 by 2070, and under what conditions do they become vulnerable to missing it?

## Important framing

The variables we have are mostly **model outputs**, not original model inputs.

So we should not say:

> These variables cause net zero.

We should say:

> These reported pathway characteristics are associated with reaching or missing net-zero CO2 by 2070.

This keeps the analysis scientifically defensible.

## Research question

**Under what combinations of pathway characteristics do global scenarios reach net-zero CO2 by 2070, and under what combinations do they become vulnerable to missing it?**

## Variables of interest

### Main outcome variable

**success_nz2070**

* `1` = scenario reaches global net-zero CO2 by 2070
* `0` = scenario does not reach global net-zero CO2 by 2070

### Main vulnerability variable

**failure_nz2070**

* `1` = scenario misses global net-zero CO2 by 2070
* `0` = scenario reaches global net-zero CO2 by 2070

### Robustness outcome

**sustained_success_nz2070**

* `1` = scenario reaches net zero by 2070 and stays at or below zero afterwards
* `0` = scenario misses net zero or rebounds above zero later

## Pathway variables to analyse

We use these variables as **pathway descriptors**:

* **2030 CO2 emissions**
* **2040 CO2 emissions**
* **2050 CO2 emissions**
* **2050 fossil primary energy**
* **2050 non-biomass renewables**
* **2050 final energy electricity**
* **2050 biomass**
* **2050 nuclear**
* **2050 geological carbon storage**
* **2070 geological carbon storage**
* **2100 CO2 emissions**
* **1.5°C exceedance probability**, if available

## Derived variables

We can also create extra pathway features:

* **CO2 reduction from 2020 to 2030**
* **CO2 reduction from 2030 to 2050**
* **Fossil decline from 2020 to 2050**
* **Renewables growth from 2020 to 2050**
* **Electrification growth from 2020 to 2050**
* **Carbon storage reliance by 2050 or 2070**

## Step-by-step workflow

### Step 1: Build the scenario-level dataset

Each row should be one **model-scenario combination**.

Keep:

* model name
* scenario name
* emissions values
* energy-system variables
* net-zero outcome labels

Final output of this step:

**one clean dataset for analysis**

### Step 2: Define success and failure

For every scenario, identify whether it reaches **global net-zero CO2 by 2070**.

Create:

* **success_nz2070**
* **failure_nz2070**
* **sustained_success_nz2070**

This gives us the core decision outcome.

### Step 3: Do descriptive analysis first

Before using PRIM or CART, compare successful and failed scenarios.

Plots to make:

* **CO2 trajectories for success vs failure**
* **2030 CO2 by success/failure**
* **2050 fossil energy by success/failure**
* **2050 renewables by success/failure**
* **2050 electricity by success/failure**
* **Carbon storage by success/failure**

Purpose:

**Build intuition before algorithmic scenario discovery.**

### Step 4: Build the decision structure

We classify the scenario space into three decision regions.

### Safe or robust region

Scenarios that reach net zero by 2070 under clear pathway conditions.

### Vulnerable region

Scenarios that miss net zero by 2070 and share common warning signs.

### Ambiguous or transition region

Scenarios that are close to the boundary, rely heavily on late reductions, or reach net zero only with strong carbon storage or net-negative emissions.

This is the main decision framing.

### Step 5: Use PRIM to find vulnerability boxes

PRIM should first focus on **failure**.

Target:

**failure_nz2070 = 1**

Question:

**Where in the pathway space are failures concentrated?**

Example vulnerability box:

* 2030 CO2 remains high
* 2050 fossil energy remains high
* renewable growth is weak
* electrification is slow
* carbon storage is insufficient or delayed

PRIM outputs to report:

* **Density**: how many scenarios inside the box are failures
* **Coverage**: how many total failures the box captures
* **Mass**: how much of the full ensemble sits inside the box
* **Restricted dimensions**: which variables define the vulnerability box

### Step 6: Use PRIM to find success boxes

Then run PRIM for **success**.

Target:

**success_nz2070 = 1**

Question:

**Where in the pathway space are successful scenarios concentrated?**

Example success box:

* 2030 CO2 is already lower
* 2050 fossil energy is much lower
* renewables are higher
* electrification is stronger
* carbon storage or removals support the final transition

### Step 7: Use CART as an easy-to-explain decision tree

CART gives simple rules.

Target:

**success_nz2070**

Example rule:

> If 2030 CO2 is below X and 2050 fossil energy is below Y, then most scenarios reach net-zero CO2 by 2070.

Or:

> If 2030 CO2 is above X and 2050 fossil energy is above Y, then scenarios are vulnerable to missing net zero by 2070.

CART is mainly for **communication**.

PRIM is our main **scenario-discovery method**.

### Step 8: Test robustness

Check whether the story changes when we change the definition.

Robustness checks:

* **Net zero by 2050**
* **Net zero by 2060**
* **Net zero by 2070**
* **Simple net zero vs sustained net zero**
* **With carbon storage variables**
* **Without carbon storage variables**
* **Excluding 2070 CO2 as an explanatory variable to avoid circularity**

This makes the result more defensible.

### Step 9: Final interpretation

Our final message should be:

**Net-zero-by-2070 scenarios are not randomly scattered across the ensemble. They occupy identifiable regions of the pathway space.**

Scenarios look less vulnerable when they combine:

* **early CO2 reductions**
* **mid-century fossil decline**
* **renewable growth**
* **electrification**
* **credible carbon-storage or net-negative capacity**

Scenarios look vulnerable when:

* **2030 emissions remain high**
* **2050 fossil energy remains high**
* **renewables/electrification lag**
* **the pathway depends too heavily on late-century compensation**

## Key caveat

These are **associations in a scenario ensemble**.

They are not:

* causal claims
* probabilities
* predictions of the future

We should not say:

> 481 out of 1564 scenarios means a 31% chance of success.

We should say:

> In this scenario ensemble, reaching net-zero CO2 by 2070 is associated with specific pathway characteristics.

## Final one-line pitch

**We use PRIM and CART to turn the Scenario Compass ensemble into a decision-relevant map of where global net-zero-by-2070 pathways look robust, where they look vulnerable, and which pathway characteristics separate the two.**
