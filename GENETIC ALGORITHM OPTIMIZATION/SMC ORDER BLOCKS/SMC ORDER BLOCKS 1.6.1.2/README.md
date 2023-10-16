### GENETIC ALGORITHM OPTIMIZATION GAO
#### OPTIMIZATION STANDARDIZATION ON CONFIG SETUP INPUTS
 - **TIMEFRAME** - M15
 - **Data Modeling** - M1 OHLC
 - **DATES** - 01.01.2020 TO 15.10.2023 (LAST 3 YEARS)
 - **OPTIMIZATION CRITERION**: FBGAO - Fast Based Genetic Algorithm + Complex Criterion Max
 - **LOTS**: 1, 10 and 100 (3 tests at 99.99 score on the optimizer)
 - **ACCOUNT SIZE**: 100,000.00 USD
 - **LEVERAGE**: 1:100
- 
#### UNDERSTANDING GAO RESULTS

The following values are displayed for each optimization run:
- Pass — the number of the testing run;
- Result — the resulting value of the parameter that is the optimization criterion for selecting the best runs;
- Profit — profit/loss received after the run;
- Total trades — the total number of trades (deals that resulted in fixing a profit or loss) executed for the run;
- Profit factor — the ratio of the total profit to the total loss in percents. A value of one means that these parameters are equal;
- Expected payoff — a statistically calculated value that reflects the average profitability/loss of one trade;
- Drawdown — the relative drawdown of equity, the largest loss in percents from the maximal value of equity. Withdrawal of assets by an Expert Advisor during optimization is taken into account during drawdown calculation;
- Recovery factor — this parameter displays the risk level of the strategy (the funds that are put to risk to earn the obtained profit). It is calculated as the ratio of gained profit to the maximum drawdown;
- Sharpe Ratio — a classic measure which is commonly used to evaluate the performance of a portfolio manager, fund results or a trading system. The ratio is calculated as (Return – Risk-Free Rate)/Standard Deviation of Return. In the strategy tester, the Risk-Free Rate is assumed to be zero. The ratio values are usually interpreted as follows:
- Sharpe Ratio < 0 — the strategy is unprofitable. Bad.
- 0 < Sharpe Ratio  < 1.0 — the risk does not pay off. Such strategies can be considered when there are no alternatives. Indefinite.
- Sharpe Ratio ≥ 1.0 — this can mean that the risk pays off and that the portfolio/strategy can show results. Good.
- Sharpe Ratio ≥ 3.0 — a high value indicates that the probability of obtaining a loss in each particular deal is very low. Very good.

#### OPTIMIZATION CRITERION

##### Optimization Type

**Fast Genetic Algorithm**

This type of optimization is based on the genetic algorithm of search for the best values of input parameters. This type is much faster than the first one and is almost of the same quality. The slow complete optimization that would take several years can be performed within several hours using the genetic algorithm.

Each individual has a specific set of genes which corresponds to the set of their parameters. Genetic optimization is based on the constant selection of the most "adapted" parameters (values that give the best result). In the general form, the algorithm can be represented the following way:
- From the total number of all possible combinations of parameters, two populations (sets) are selected by a random sample;
- Both sets are tested and the one with the best results (according to the optimization criterion) is left;
- The set members are randomly crossed with one another, undergoing random mutations and inversions of parameters;
- The descendants are sorted out by the best results, and crossing repeats;
- Sorting and crossing operations are repeated as long as there is improvement of results (the best result among descendants is better than the best one among the parents). If the optimization criterion values are not improved during several crossings (generations), the optimization process is completed.

**Number of Test Runs**

During the genetic optimization, the number of test runs is much lower, which provides quickness of optimization. After the start of the genetic optimization, an estimated number of test runs is displayed on the Settings tab. It is calculated by the following formula:

**Population size * (Unconditional number of generations + Number of generations for convergence estimation)**

where:
- Population size is calculated based on the number of possible combinations of optimization parameters, may range from 64 to 256;
- Unconditional number of generations may range from 15 to 31. It is defined by the presence of optimization criterion improvement. 15 generations are tested in all optimizations. If a generation within the range between 15 and 31 does not have any improvement of the optimization criterion, an additional test of the next generations is started for convergence estimation.
- Number of generations for convergence estimation is calculated as one third of the unconditional number of generations. If the unconditional number of generation is 18 (the 17-th generation has shown the best result and there are no improvements shown by the 18-th generation) then another 5 generations are tested: the 18-th generation has not shown any improvement, and for the estimation of convergence we need 18/3 = 6 generations without improvements of the optimization criterion. If there are no improvements shown by the specified number of generations, optimization is stopped.

- If the total number of optimization steps exceeds 1,000,000 in a 32-bit system or 100,000,000 in a 64-bit system, the genetic optimization mode starts automatically.
- During the genetic optimization, intermediate results are saved in cache after the calculation of each generation (in a file platform_data_folder/tester/cache/*.gen). Thus the optimization process can be interrupted at any time. Even if the process of genetic optimization is interrupted as a result of an external factor (for example, power failure), the optimization will be automatically continued from the last calculated generation at the next start. The genetic optimization cache is stored until the optimization settings are changed or the optimization process is completed.
•At a regular optimization stop (when you press the Stop button) all the previously calculated runs are saved. When the optimization process is resumed, it continues from the last calculated run.

**Optimization Criterion**

An optimization criterion is a certain factor, which value defines the quality of a tested set of parameters. The higher the value of the optimization criterion, the better the testing result with the given set of parameters. Such a factor can be selected in a field to the right of "Optimization" on the Settings tab.


We only use "Complex Criterion max". This is an integral and complex measure of a test pass quality. It measures multiple parameters:
- Number of Deals
- Drawdown
- Recovery Factor
- Expected Payoff
- Sharpe Ratio

By using this criteria, you can see that the highest value of one parameter (for example the profit) is not always the best option in terms of the complex analysis. The complex criterion gradually selects the best passes: firstly, by the number of deals, then by the Expected Payoff, Recovery Factor, and so on. The new option allows reception of the best optimization passes according to all parameters. Furthermore, you can select the optimal pass based on the desired parameter, such as the highest profit.