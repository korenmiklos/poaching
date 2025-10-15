# Customer Poaching and Business Stealing

## Project Overview

This project examines customer poaching in B2B relationships when key employees move between competing firms. Using Hungarian administrative data linking VAT transactions to employer-employee records, the project identifies whether buyers follow key employees (managers and professionals) to their new firms, and quantifies the economic value of these personal relationships.

## Research Question

When a key employee moves from supplier A to supplier B, do buyers of supplier A follow that employee to supplier B? This reveals whether customer relationships are primarily:
- Firm-specific (tied to brand, technology, organizational capital)
- Person-specific (tied to individual relationships, trust, expertise)

## Core Mechanism

The economic mechanism centers on buyer choice. When a key employee moves, buyers must decide whether to:
1. Stay with the original supplier (valuing firm-specific assets)
2. Follow the employee to the new supplier (valuing relationship-specific assets)

The model distinguishes between private value (firm profits) and social value (overall welfare), addressing whether customer following is efficient or merely redistributive.

## Theoretical Framework

### Discrete Choice Model with Rapport

Supplier $i$ can serve buyer $j$ at price $p_{ij}$. Transactions require personal interaction with manager $m$, generating a person-buyer specific rapport $\kappa_{mj}$. Buyers choose supplier $i$ if:

$$
p_{ij}/\kappa_{mj} \le p_{kj}/\kappa_{m'k}
$$

for all potential suppliers $k$ with managers $m'$.

### Key Modeling Assumptions

1. **Rapport distribution**: Manager-buyer rapport follows a Frechet distribution with parameter $T_m$ (function of manager observables)
2. **Bayesian updating**: After observing past supplier choices, buyers update beliefs about manager rapport
3. **Selection mechanism**: Managers selected from tough competition must have higher unobserved rapport
4. **Conditional Frechet**: Past winners have rapport distributed Frechet with parameter $\Lambda_m = T_m/\pi_{ij}$, where $\pi_{ij}$ is the ex-ante probability of selection

### Identification Strategy

The model identifies rapport quality through the conditional probability of past selection. If an employee's firm had low ex-ante probability of winning ($\pi_{ij}$) but won anyway, this signals high unobserved rapport. The coefficient on "worked together before" equals $-\ln(\pi_{ij})$.

Key testable implication: managers from "unlikely" suppliers (low $\pi_{ij}$) should have larger positive effects when they move, because their past selection revealed higher unobserved rapport.

## Data

### Administrative Data Sources

1. **VAT data (2015-2022)**: Transaction-level buyer-supplier relationships
2. **Linked employer-employee data (2002-2021)**: Worker mobility across firms with occupation codes
3. **Overlap period (2015-2021)**: Joint analysis of transactions and mobility

### Data Quality

- Comprehensive coverage from 2018 onwards
- Earlier years (2015-2017) truncated from below due to reporting thresholds
- High-quality firm-worker-buyer linkage
- FEOR occupation codes distinguish client-facing roles

### Key Employee Definition

Managers and professionals (FEOR codes) with customer-facing roles, distinguished from production workers. Occupation selection based on higher education requirement and customer contact requirements.

## Empirical Findings

### Main Results

- **Any employee effect**: ~1% increase in probability of buyer-supplier relationship when any employee has moved between firms
- **Key employee effect**: ~3% increase when managers/professionals move
- **Persistence**: Effects remain when conditioning on buyers who have never worked with the destination firm before
- **Occupational heterogeneity**: Manager/professional effects (2pp) exceed production worker effects (0.6-0.8pp)
- **Strong personal relationships**: In 2% of buyer-seller relationships, buyer has past connection with manager; this increases purchase probability by 4pp relative to 0.01% baseline (400-fold increase)

### Empirical Specification

The analysis uses difference-in-differences and event study designs comparing:
- Buyers of sending firm (treatment group)
- Control buyers (never worked with either firm)
- Differential effects by worker occupation type

The preferred specification uses complementary log-log (cloglog) regression to estimate proportional hazards of starting a new buyer-supplier relationship, consistent with the underlying Frechet distribution.

## Model Extensions

### Multiple Managers
With $n$ managers at firm $i$, the effective Frechet parameter becomes $\sum_m T_m = nT_m$ (for symmetric managers). Buyers are more likely to purchase from firms with more managers. When one manager moves, probability $1/n$ that this was the buyer's actual contact. Non-selected managers have worse conditional rapport distribution.

### Past Losers
Managers who lost previous competitions have conditional rapport distribution:

$$
\Pr(\kappa_{nj} \le K|n \text{ lost}) = \frac{e^{-T_n K^{-\theta}} - \pi_{nj} e^{-T_n K^{-\theta}/\pi_{nj}}}{1-\pi_{nj}}
$$

This is a mixture distribution, not pure Frechet. Past losers compete at a disadvantage unless observables change substantially.

### Switching Suppliers
When the manager from winning supplier 1 moves to losing supplier 2, and supplier 1 gets a new random manager, the probability of switching is:

$$
\pi_{21} = \frac{1 - \pi_{10}}{1 - \pi_{10} + \pi_{10}^2}
$$

where $\pi_{10}$ is the past probability of choosing supplier 1. This is non-linear in past probabilities.

## Outstanding Research Agenda

### Theoretical
1. Fully characterize model with multiple past losers and common competitors
2. Incorporate dynamic frictions and switching costs
3. Extend to multiple key employees per firm with heterogeneous skills

### Empirical
1. Structural estimation of rapport parameters and dispersion ($\theta$)
2. Test key prediction: managers from unlikely suppliers should have larger effects
3. Validate reduced-form results with full 2018-2021 clean data
4. Explore COVID-19 as exogenous relationship disruption
5. Industry heterogeneity in key employee importance

### Welfare Analysis
1. Decompose private vs. social value of customer following
2. Assess efficiency of customer reallocation
3. Evaluate non-compete clause policies using the model framework
4. Compare relationship capital to other forms of intangible capital

## Policy and Business Applications

### Policy Relevance
1. **Non-compete agreements**: Model framework can evaluate effects of restricting employee mobility on competition and efficiency
2. **Industry regulation**: Sectors with high key employee effects may require different antitrust approaches
3. **Competition policy**: Distinguish when customer poaching enhances vs. reduces competition

### Business Applications
- Identifies value of hiring managers with established client relationships
- Quantifies retention incentives for key client-facing employees
- Provides framework for customer retention strategies during employee departures
- Administrative data provides insights unavailable to individual firms

## Methodological Contributions

1. Novel application of extreme value theory (Frechet distributions) to B2B relationship formation
2. Creative use of employee mobility as natural experiment
3. Bayesian updating framework for learning about unobserved relationship quality
4. Selection-correction method using conditional extreme value distributions
5. Framework applicable to procurement, professional services, and other matching contexts

## Literature Context

Limited existing work combines:
- Rigorous economic model of B2B relationships
- Person-level variation in customer following
- Administrative data linking workers, firms, and transactions
- Welfare analysis distinguishing private and social value

Most business literature on customer poaching lacks optimization-based frameworks. Recent economics papers on firm-employee relationships typically focus on productivity, not customer relationships. This project fills an important gap.

## Data Structure

The project uses `bead` for data management:
- **Input data** (`input/`): VAT transactions, linked employer-employee data
- **Temporary files** (`temp/`): Intermediate data processing
- **Output** (`output/`): Final tables, figures, regression results
- **Code** (`code/`): Stata .do files for data wrangling and analysis

The empirical analysis is implemented in Stata following difference-in-differences and event study designs. All scripts are callable from command line via Makefile targets.
