# Poaching Project Summary

## Research Question and Mechanism

### Main Research Question
The project studies customer poaching - specifically examining how key employees moving between firms affect buyer-supplier relationships. The core question is: when a key employee moves from one supplier to another, do buyers follow that employee to the new firm?

### Economic Mechanism
The mechanism centers on the value of personal relationships versus firm-specific assets in B2B transactions. The key insight is that **the buyer is the decision maker** who must choose between:
- Staying with the original supplier (firm loyalty/brand/technology value)
- Following the key employee to their new firm (relationship/trust value)

The project aims to distinguish between:
- **Private value**: Individual firm profits from retaining/gaining customers
- **Social value**: Overall welfare implications of customer mobility

## Modeling Approach

### Core Framework
The model uses a **discrete choice framework with Gumbel-distributed shocks**:

- Supplier i can supply at price P
- Key employees add/subtract from base price through a "rapport" parameter
- Buyers face idiosyncratic preference shocks (Gumbel distributed)
- Decision becomes: should buyer switch when key employee moves?

### Key Model Features
1. **Rapport Parameter**: Captures relationship-specific value orthogonal to productivity and wages
2. **Conditional Logit Structure**: Uses "shifted Gumbel" distributions for employees with known history
3. **Updated Beliefs**: Bayesian updating of rapport based on past performance
4. **Selection Identification**: Unlikely winners reveal higher unobserved quality

### Identification Strategy
The model identifies rapport quality through **conditional probability of past selection**:
- If an employee's firm had low observable probability of winning but won anyway, this signals high unobserved rapport
- Coefficient on "worked together before" dummy equals minus log of past selection probability
- More surprising past victories imply larger positive effects in future competitions

## Data Available

### Primary Datasets
1. **VAT Data (2015-2022)**: Buyer-supplier transactions with firm identifiers
2. **Linked Employer-Employee Data (2002-2021)**: Worker flows between firms
3. **Overlap Period (2015-2021)**: Combined analysis possible

### Data Quality Features
- Early years (2015-2017) truncated from below due to reporting thresholds
- From 2018 onwards: comprehensive coverage
- High-quality linkage between worker movements and customer relationships
- Occupation codes allow identification of client-facing roles

## Key Findings from Preliminary Analysis

### Empirical Results
- **Baseline Effect**: ~1% increase in probability of working with firm when any employee has moved between firms
- **Key Employee Effect**: ~3% increase when specifically key employees move (managers/professionals with customer-facing roles)
- **Robustness**: Effect persists even conditioning on firms buyer hasn't worked with before

### Definition of Key Employees
Currently defined as: managers and professionals with customer-facing roles, distinguished from production workers who show minimal customer-following effects.

## Identification Strategy

### Model-Based Identification
1. **Past Performance as Instrument**: Use probability of past contract wins to identify unobserved rapport quality
2. **Occupational Variation**: Leverage difference between key employees (high effect) vs. production workers (low effect)
3. **Firm Controls**: Condition on never having worked with the firm before to isolate employee effects

### Assumptions
- **Observable Selection**: Econometrician observes same information as decision-maker except rapport
- **Rapport Persistence**: Winners maintain their rapport realization; losers draw new rapport (modeling assumption)
- **Independent Mobility**: Employee moves are exogenous to buyer-specific relationships

## Potential Welfare and Policy Implications

### Welfare Analysis
- **Efficiency Question**: Is customer following socially optimal or just privately profitable?
- **Market Stealing**: One firm expands while others shrink - net welfare unclear
- **Relationship Capital**: If rapport reflects genuine productivity, following employees may be efficient

### Policy Applications
1. **Non-Compete Clauses**: Model can evaluate effects of restricting employee mobility
2. **Industry Regulation**: Sectors with high key employee effects may warrant different policies
3. **Competition Policy**: Understanding when customer poaching enhances vs. reduces competition

### Practical Business Relevance
- High business interest due to direct profit implications
- Unique administrative data provides insights unavailable to private firms
- Model framework applicable across industries with varying key employee importance

## Outstanding Research Tasks

### Theoretical Development
1. Fully work out the model with "losers" (employees who lost previous competitions)
2. Extend to multiple key employees per firm
3. Add dynamic frictions/switching costs

### Empirical Implementation
1. Implement structural estimation of rapport parameters
2. Validate reduced-form results with longer, cleaner data
3. Explore COVID-19 as exogenous shock disrupting established relationships

### Extensions
1. Industry heterogeneity in key employee importance
2. Cross-country analysis (potential with German data)
3. Connection to non-compete agreement natural experiments

## Academic and Policy Context

### Literature Position
- Limited existing work on customer poaching with proper economic models
- Most business literature lacks optimization-based frameworks
- Recent papers emerging but not addressing key questions with appropriate methodology

### Methodological Contribution
- Novel application of discrete choice models to B2B relationships
- Creative use of employee mobility as identification strategy
- Framework potentially applicable to procurement and other matching contexts

The project represents a significant methodological advance in understanding B2B relationship dynamics with clear policy relevance and strong empirical foundations.
