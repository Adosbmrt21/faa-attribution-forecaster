# FAA outage attribution forecaster

Entry for make.fun bounty `polymarket-faa-attribution-02`: forecast the Yes
price of every market in Polymarket's FAA outage attribution family (Iran /
foreign actor / hack / AI sandbox escape) at every minute of the 4 hours
after each checkpoint, as five quantiles (5/25/50/75/95%), scored by mean
pinball loss.

`main.py` (Python 3.13, standard library only) reads one case file
(`makefun/polymarket-case/v1`) per run and writes one forecast file. Per
market it builds empirical change-quantiles from the market's own last 720
minutes at anchor horizons, interpolates them in sqrt(h) space, and blends
them with the house baseline's flat random-walk spread by how hot the
market has been lately. Deterministic: two runs of a case agree byte for
byte.
