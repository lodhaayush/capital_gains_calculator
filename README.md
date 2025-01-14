# UK capital gains calculator

[![CI](https://github.com/lodhaayush/capital_gains_calculator/workflows/CI/badge.svg)](https://github.com/lodhaayush/capital_gains_calculator/actions)

Calculate capital gains tax by transaction history exported from Schwab and generate PDF report with calculations. Automatically convert all prices to GBP and apply HMRC rules to calculate capital gains tax: "same day" rule, "bed and breakfast" rule, section 104 holding.

## Report example

[calculations_example.pdf](https://github.com/lodhaayush/capital_gains_calculator/blob/main/calculations_example.pdf)

## Setup

On Mac:
```shell
brew install --cask mactex-no-gui
pip3 install jinja2
```

## Usage

- Change constants on the top of `calc.py`, e.g. tax year, allowance, filenames.
- `schwab_transactions.csv`: the exported transaction history from Schwab since the beginning. Or at least since you first acquired the shares, which you were holding during the tax year. You can probably convert transactions from other brokers to Schwab format.
- `GBP_USD_monthly_history.csv`: monthly GBP/USD prices from [gov.uk](https://www.gov.uk/government/collections/exchange-rates-for-customs-and-vat).
- `initial_prices.csv`: stock prices in USD at the moment of vesting, split, etc.
- Run `python3 calc.py`

## Testing
```shell
python3 calc.py > test_output.txt
diff test_output.txt sample_output.txt
```
If you are adding a new feature, please update `sample_transactions.csv` and `sample_output.txt`.

## Disclaimer

Please be aware that I'm not a tax adviser so use this software application at your own risk.

## Contribute

If you notice any bugs feel free to open an issue or send a PR.
