# Limitations & Roadmap

This is a working prototype. The architecture is sound and the model is real, but the data sample is small and several measures need refinement before the numbers should be read as production-grade. Documenting that line honestly is part of the work. A dashboard is only as trustworthy as the model and data under it.

## Known limitations

1. **Sample size.** The organizational financial sample is 23 organizations, with tax years 2021 and 2022. The economic dataset covers 2008 to 2023. The organizational sample demonstrates the architecture but is not yet large enough to support long-term organization-level trend claims.
2. **Yearly aggregation.** A yearly giving-and-economics table repeats the same organizational totals across years. Those should not be read as actual historical annual organizational totals until more filing years are loaded.
3. **Missing data handling.** A missing GivingUSA value for 2023 should return blank in its year-over-year calculation rather than an artificial negative 100 percent. Nulls need to be distinguished from zeros throughout.
4. **Inflation adjustment.** The real-giving measure currently deflates by a single year's inflation rate. Valid multi-year real-dollar comparison needs a cumulative price index.
5. **Index calculation.** A GivingUSA index that reads as constant across years points to a calculation or filter-context issue to resolve.
6. **Zero fundraising expense.** Organizations reporting zero fundraising expense produce an undefined ratio. That should resolve to blank, not to an ordinary result.
7. **Scenario model.** The GDP, inflation, and unemployment formulas are assumptions, not statistically validated relationships. They need sensitivity analysis and historical backtesting before they carry forecasting weight.

## Validation plan

Before treating the model as production-ready, I would run a formal validation pass:

| Validation area | What to verify |
| --- | --- |
| Source integrity | All expected XML records were processed |
| Entity integrity | EINs identify organizations consistently |
| Financial integrity | Extracted totals match source filings |
| Temporal integrity | Tax years map correctly to economic years |
| Relationship integrity | Filters propagate as intended |
| Calculation integrity | Ratios and measures return expected results |
| Missing data | Nulls are distinguished from zeros |
| Forecast integrity | Assumptions and model limits are documented |
| Presentation integrity | Slicers and visuals return consistent results |

## From prototype to platform

The current build is a desktop analytical prototype. The design already anticipates its own growth. The evolution toward a reproducible, governed platform:

| Current implementation | Potential future architecture |
| --- | --- |
| Local XML files | Automated source ingestion |
| Power Query transformations | Version-controlled ETL pipelines |
| Power BI model | Governed semantic model |
| Excel economic dataset | Automated economic data ingestion |
| DAX scenario calculations | Validated statistical forecasting service |
| PBIX report | Published reporting environment |
| Manual refresh | Scheduled orchestration |
| Manual validation | Automated data-quality tests |

The point is not that every component here is already built. It is that the current implementation is structured so it can grow into them without a rebuild.
