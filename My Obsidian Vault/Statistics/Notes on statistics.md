# Summaries
## Cluster Analysis

In machine learning and statistics, cluster analysis serves as an initial discovery tool to sort data points into distinct sets based on how much they have in common. Rather than using pre-existing categories, the algorithm discovers groupings dynamically depending on your inputs and analytical goals. It essentially transforms dense, multi-dimensional data into clearer, high-level trends.

At its core, this approach aims to deliver:

- Uniformity within individual groups, where members closely resemble one another.

- Clear boundaries between groups, ensuring separate clusters remain distinct.

- A simplified picture of complex data structures.

Because this technique is designed for exploration, it works well for spotting trends, brainstorming hypotheses, and building preliminary models. However, it comes with clear limitations and cannot prove:

- Cause-and-effect connections between variables.

- Whether observed differences carry true statistical weight.

- That the identified groups will remain stable over time.

- An absolute or single correct way to categorize the data.

- Reliable predictions for new, unseen data points.

> **Source:** [Research Method - Cluster Analysis](https://www.google.com/search?q=https://researchmethod.net/cluster-analysis/)

## Factor Analysis

Factor analysis is a statistical technique used to simplify complex datasets by grouping correlated variables under broader, unmeasured concepts known as **latent factors**. While observed variables (like test scores or survey answers) are directly recorded, latent factors are underlying traits inferred from how those direct measurements move together. Researchers primarily rely on this approach to streamline data, build measurement tools, and verify theoretical frameworks.

### Core Mathematical Framework

The method translates a matrix of correlations into a streamlined structural model:

$$x = \Lambda f + \varepsilon$$

- **Observed Variables ($x$):** The direct data points collected during measurement.

- **Factor Loadings ($\Lambda$):** Coefficients reflecting the strength of the relationship between a specific metric and an underlying factor.

- **Latent Factors ($f$):** The hidden, underlying constructs driving the shared patterns.

- **Unique Variance and Error ($\varepsilon$):** The portion of data specific to a single measurement alongside residual noise.

### Understanding Variance Breakdown

When examining standardized variables, factor analysis divides total variance into two key components:

**Common Variance (Communality):** The portion of a variable's variation that aligns with other metrics and is successfully captured by the shared factors.

**Unique Variance (Uniqueness):** The remaining variation specific strictly to that single indicator, including measurement errors and isolated influences not explained by the model.

> **Source**: [Research Method - Factor Analysis](https://researchmethod.net/factor-analysis/)

## Multidimensional Scaling (MDS)
Here is a restructured summary tailored specifically for linguistics applications, translating the core mathematical concepts into relevant linguistic contexts:

Multidimensional Scaling (MDS) is a statistical approach that converts pairwise similarity or dissimilarity data into geometric distances on a low-dimensional map (typically 2D or 3D). By plotting items as coordinates, MDS helps researchers visualize complex relationships that are otherwise hard to spot in a raw distance matrix.

### Linguistic Applications and Context

While MDS is used across many fields, it is particularly powerful in linguistics for mapping items based on perceptual or behavioral relationships rather than fixed feature lists:

- **Dialectology and Language Variation:** Mapping lexical or phonetic distances between geographical dialects (e.g., reconstructing a language family tree or dialect continuum on a spatial grid without needing GPS coordinates).

- **Phonetics and Phonology:** Visualizing perceptual spaces, such as plotting vowel spaces based on native listeners' confusion matrices or acoustic spectral distances rather than raw formant frequencies.

- **Semantics and Psycholinguistics:** Mapping word associations, semantic fields, or cross-linguistic lexical similarities based on speaker judgments or co-occurrence data.

### Core Concepts: Similarity, Dissimilarity, and Distance

MDS processes relational data by converting comparisons into spatial metrics:

- **Similarity:** Increases as two linguistic items share more traits (e.g., shared cognate percentages or co-occurrence frequencies).

- **Dissimilarity:** Increases as items diverge (e.g., acoustic dissimilarity between consonant sounds). These values do not always meet formal mathematical rules for physical space.

- **Distance:** The resulting geometric space, which ideally satisfies mathematical rules (non-negativity, symmetry, zero distance to self, and the triangle inequality). If linguistic input data violates these rules (e.g., asymmetric listener perception where Sound A is misheard as Sound B more often than vice-versa), some MDS algorithms can still accommodate the distortion.

### Data Requirements

To run an MDS model, researchers typically compile an $n \times n$ proximity matrix representing $n$ linguistic items, which requires:

- Matching rows and columns representing the same set of linguistic units.

- Diagonal values set to zero (comparing an item to itself).

- Non-negative values across off-diagonal positions.

- Symmetrical entries (when reciprocal relationships are assumed) and a clear, documented method for how similarity scores were derived.

> **Source:** [Research Method - MDS](https://www.google.com/search?q=https://researchmethod.net/multidimensional-scaling/)
