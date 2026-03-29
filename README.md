# Engeto Hackathon Mortgage Refinance Calculator

This repository contains a Streamlit prototype created during the ENGETO hackathon focused on financial literacy.

The project helps users reason about mortgage refinancing after a fixation period. Instead of comparing only interest rates, it also looks at monthly cashflow and simulates what happens if the payment difference is invested over time.

The project won the hackathon. Coverage of the result and product idea is available here:
https://zpravy.kurzy.cz/791857-vitezem-hackathonu-se-zamerenim-na-financni-gramotnost-se-stal-tym-ktery-vytvoril-kalkulacku-pro/

## What the app does

The Streamlit app lets the user enter:

- original mortgage amount
- original mortgage term
- original interest rate
- refinancing year
- new interest rate after refinancing
- new mortgage duration
- preferred investment risk profile: `safe`, `medium`, or `risky`

From those inputs, the app:

- calculates the original amortization schedule
- simulates refinancing at the chosen year
- recalculates the remaining mortgage using the new rate and duration
- compares original and new monthly payments
- estimates total interest paid
- tracks remaining balance over time
- simulates investing the monthly payment difference after refinancing
- displays charts and a monthly data table

## Main idea

The core product idea from the hackathon was to answer a more realistic question than a standard refinance calculator:

Should I refinance my mortgage and, if that changes my monthly payment, would I be better off using the difference for investing and potentially earlier payoff?

The codebase represents this through three simple investment scenarios:

- `safe`
- `medium`
- `risky`

## Project structure

- [main.py](/home/flaim/www/EngetoHackathon/main.py)  
  Streamlit entrypoint and user interface.

- [loan_with_refinancing.py](/home/flaim/www/EngetoHackathon/loan_with_refinancing.py)  
  Extends the mortgage schedule with a refinance event and optional investment simulation.

- [investor.py](/home/flaim/www/EngetoHackathon/investor.py)  
  Tracks portfolio growth for the three investment profiles.

- [investing_strategies.py](/home/flaim/www/EngetoHackathon/investing_strategies.py)  
  Investment-return logic. At the moment, this is effectively a simplified placeholder with fixed annual returns.

- [taxes.py](/home/flaim/www/EngetoHackathon/taxes.py)  
  Helper for aggregating tax deductions from mortgage interest.

- [cnb_interest_rates.py](/home/flaim/www/EngetoHackathon/cnb_interest_rates.py)  
  Utility for fetching Czech National Bank rates. This is not currently wired into the Streamlit UI.

- `test_*.py`  
  Unit tests for the refinance, investing, taxes, and rate-fetching logic.

## Running locally

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Start the Streamlit app:

```bash
streamlit run main.py
```

## Running tests

```bash
pytest
```

## Notes

- The app is a hackathon prototype, not a production-grade financial advisory tool.
- The investment model is simplified and currently uses fixed returns instead of live market-derived values.
- The CNB rates integration exists separately in the codebase but is not yet connected to the main app flow.
- Mortgage tax treatment is represented in a simplified way and should not be treated as tax advice.
