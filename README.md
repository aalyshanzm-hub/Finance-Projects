I built a macro regime sector-rotation model in Python. The idea is that different parts
of the equity market lead at different points in the economic cycle — tech when growth
is strong and inflation is quiet, energy and utilities when it's the other way round — and
I wanted to test whether you could turn that intuition into a systematic rule rather than
a gut call.
It works in four stages. First I pull six FRED macro series — industrial production, payrolls, unemployment, 
retail sales, CPI and PPI — and convert each into YoY momentum, then standardize them into a growth score and an inflation score.
Second, the signs of those two scores put each month into one of four regimes:
Goldilocks, Reflation, Stagflation or Deflation. I cross-check the labels against a
Gaussian mixture clustering as a sanity test — they agree about 75% of the time. Third,
for each month I look at how each of nine sector ETFs performed in past months of that
same regime and tilt away from equal weight toward the stronger ones, long-only and
capped at 30%. Fourth, I backtest it monthly against SPY and against equal weight, net
of 7.5 basis points of transaction cost.
The part I'd point to is the look-ahead discipline — expanding-window standardization,
a one-month publication lag on the macro data, and weights lagged before they're
applied to returns. Three separate places where it's easy to accidentally cheat.
Right now it runs on a synthetic macro feed so it executes without API keys, and it
produces about 1.4% annualized alpha with an information ratio of 0.23 — which,
honestly, over 200 months isn't statistically significant.
