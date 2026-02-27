# Decision Quality Metrics

A comprehensive framework for measuring, tracking, and improving the quality of decisions across organizations and teams. This library provides quantitative metrics, KPIs, and analytical tools that transform decision-making from a subjective art into a measurable discipline.

## Overview

Most organizations invest heavily in execution but rarely measure the quality of the decisions that drive that execution. Decision Quality Metrics bridges this gap by providing a systematic approach to evaluating decisions both before they are made (process quality) and after outcomes are known (outcome analysis).

The framework draws on proven [decision-making principles](https://keeprule.com/en/principles) established by leading thinkers in judgment and choice, translating their insights into quantifiable metrics that teams can track over time.

## Features

- **Decision Scorecard**: Rate decisions across six quality dimensions
- **Process Quality Index**: Measure the rigor of your decision-making process
- **Outcome Tracking**: Record and analyze decision outcomes over time
- **Calibration Testing**: Measure how well predictions match actual results
- **Brier Score Calculator**: Quantify probabilistic forecast accuracy
- **Decision Velocity Metrics**: Track how quickly decisions are made relative to their complexity
- **Regret Minimization Score**: Evaluate decisions against counterfactual alternatives
- **Team Decision Analytics**: Compare decision quality across teams and individuals
- **Trend Analysis Dashboard**: Visualize decision quality improvements over time
- **Automated Reporting**: Generate periodic decision quality reports

## Installation

```bash
pip install decision-quality-metrics
```

## Quick Start

```python
from dqm import DecisionScorecard, QualityTracker

# Create a scorecard for a specific decision
scorecard = DecisionScorecard(
    decision="Expand into Asian markets",
    decision_date="2024-03-15",
    decision_maker="strategy_team"
)

# Rate the six dimensions of decision quality (1-10)
scorecard.rate({
    "framing": 8,           # How well was the problem defined?
    "alternatives": 7,       # Were sufficient options considered?
    "information": 6,        # Was relevant information gathered?
    "values_tradeoffs": 8,   # Were tradeoffs explicitly addressed?
    "reasoning": 7,          # Was sound logic applied?
    "commitment": 9          # Was there clear commitment to action?
})

print(f"Overall Decision Quality Score: {scorecard.overall_score:.1f}/10")
print(f"Weakest dimension: {scorecard.weakest_dimension}")
print(f"Recommendation: {scorecard.improvement_suggestion}")
```

## Core Metrics

### Decision Quality Score (DQS)

The primary composite metric combining all six quality dimensions:

```python
from dqm import DQSCalculator

calculator = DQSCalculator(weights={
    "framing": 0.20,
    "alternatives": 0.18,
    "information": 0.18,
    "values_tradeoffs": 0.16,
    "reasoning": 0.16,
    "commitment": 0.12
})

dqs = calculator.compute(decision_data)
print(f"DQS: {dqs.score:.1f} ({dqs.grade})")
```

### Calibration Score

Measure how well your confidence levels match actual outcomes. This is a crucial skill emphasized by [masters of rational thinking](https://keeprule.com/en/masters) who stress the importance of knowing what you know and what you do not know.

```python
from dqm import CalibrationTracker

tracker = CalibrationTracker()

# Record predictions with confidence levels
tracker.record_prediction("Q1 revenue > $10M", confidence=0.80, actual=True)
tracker.record_prediction("Product launch on time", confidence=0.90, actual=False)
tracker.record_prediction("Customer churn < 5%", confidence=0.70, actual=True)

# Analyze calibration
report = tracker.analyze()
print(f"Calibration score: {report.score:.2f}")
print(f"Overconfidence bias: {report.overconfidence:.2f}")
print(f"Brier score: {report.brier_score:.3f}")
```

### Decision Velocity

Track the relationship between decision speed and quality:

```python
from dqm import VelocityTracker

velocity = VelocityTracker()
velocity.record({
    "decision": "Hire senior engineer",
    "complexity": "medium",
    "time_to_decision_hours": 48,
    "quality_score": 7.5
})

analysis = velocity.analyze_efficiency()
print(f"Average time for medium decisions: {analysis.avg_time_medium}h")
print(f"Quality-speed correlation: {analysis.correlation:.2f}")
```

## Advanced Analytics

### Portfolio Decision Analysis

Analyze the quality of decisions across different categories and contexts. Understanding various [decision-making scenarios](https://keeprule.com/en/scenarios) helps you benchmark your metrics against best practices for specific types of choices.

```python
from dqm import PortfolioAnalyzer

analyzer = PortfolioAnalyzer(decision_database)
portfolio = analyzer.analyze(timeframe="2024-Q1")

print(f"Total decisions tracked: {portfolio.count}")
print(f"Average DQS: {portfolio.avg_dqs:.1f}")
print(f"Best category: {portfolio.best_category}")
print(f"Needs improvement: {portfolio.worst_category}")
```

### Counterfactual Analysis

Evaluate what would have happened with alternative choices:

```python
from dqm import CounterfactualEngine

engine = CounterfactualEngine()
analysis = engine.evaluate(
    decision="chose_vendor_a",
    alternatives=["vendor_b", "vendor_c", "build_in_house"],
    outcome_data=actual_outcomes,
    market_data=market_conditions
)

for alt in analysis.alternatives:
    print(f"{alt.name}: estimated outcome = {alt.estimated_outcome}")
    print(f"  Regret score: {alt.regret_score:.2f}")
```

## Reporting

Generate comprehensive decision quality reports:

```python
from dqm import ReportGenerator

generator = ReportGenerator(decision_database)
report = generator.monthly_report("2024-03")
report.export("pdf", "decision_quality_march_2024.pdf")
report.export("markdown", "decision_quality_march_2024.md")
```

For templates and structured approaches to improving your decision metrics, explore the [decision prompts library](https://keeprule.com/en/prompts) which provides guided frameworks for each quality dimension.

## Metric Reference Table

| Metric | Range | Good | Excellent |
|--------|-------|------|-----------|
| Decision Quality Score | 0-10 | 7.0+ | 8.5+ |
| Calibration Score | 0-1 | 0.80+ | 0.90+ |
| Brier Score | 0-1 | < 0.25 | < 0.10 |
| Decision Velocity Index | 0-100 | 60+ | 80+ |
| Regret Minimization Score | 0-1 | 0.75+ | 0.90+ |

## Contributing

Contributions are welcome! We especially appreciate:

1. New metric implementations
2. Improved calibration algorithms
3. Visualization enhancements
4. Documentation improvements
5. Real-world case studies

Please fork, branch, and submit a PR with tests included.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built on decades of decision science research
- Inspired by the work of decision quality practitioners worldwide
- Designed to make decision improvement systematic and measurable
