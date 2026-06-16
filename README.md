We have a big set of climate scenarios from Scenario Compass.

Some scenarios reach global net-zero CO2 by 2070.

Some do not.

Our job is not to say which future will happen.

Our job is to find out:

What do the successful scenarios have in common?

Important point: the data we have are mostly model outputs, not original model inputs. So we should not say “this causes net zero.” We should say “scenarios that reach net zero usually have these pathway features.”

Our plan is simple:

1. Make a yes/no label

Did the scenario reach global net-zero CO2 by 2070?

Yes = success
No = failure

2. Build useful pathway features

For each scenario, we look at things like:

2030 CO2 emissions
2050 CO2 emissions
2050 fossil energy
2050 renewables
2050 electricity use
2050 or 2070 carbon storage

3. First, make simple plots

Before fancy methods, we compare success vs failure.

Do successful scenarios have lower 2030 emissions?
Less fossil energy in 2050?
More renewables?
More electrification?
More carbon storage?

This gives us the basic story.

4. Then use PRIM

PRIM finds “danger zones” or “success zones” in the scenario space.

Example:

Scenarios often fail when:

2030 CO2 is still high
2050 fossil energy is still high
renewables are low
electrification is slow

So PRIM helps us find the box where failure is concentrated.

5. Then use CART

CART gives us a simple decision tree.

Example:

If 2030 CO2 is below X
and 2050 fossil energy is below Y
then the scenario is more likely to reach net zero by 2070.

CART is useful because it gives rules that are easy to explain in the presentation.

6. Then check robustness

We test whether the story changes if we change the target:

net zero by 2050
net zero by 2060
net zero by 2070
net zero once vs sustained net zero
with carbon storage variables vs without carbon storage variables

Final message:

We should not say:

“481 out of 1564 scenarios means 31% chance of success.”

That would be wrong because the ensemble is not a probability sample.

We should say:

“In this scenario ensemble, reaching net-zero CO2 by 2070 is associated with early emissions decline, fossil phase-down, renewable growth, electrification, and some level of carbon-storage reliance.”

One-line version:

We are using PRIM and CART to turn a messy scenario database into simple, explainable rules about what kind of energy pathways reach global net-zero CO2 by 2070.
