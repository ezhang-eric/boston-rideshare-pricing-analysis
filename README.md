# Boston Rideshare Market Analysis & Pricing Optimization

## Project Overview
This project leverages a large-scale dataset of approximately 500,000 Boston ride-share records to analyze and optimize competitive pricing strategies for Uber and Lyft. By combining exploratory data analysis, stratified linear regression, and unsupervised K-Means clustering, the study identifies core price drivers and economically meaningful market segments to maximize revenue per ride.

## Key Technical Spikes

### 1. High-Scale Data Engineering & Preprocessing
* **Dataset Scale:** Processed ~500,000 observations with moderate dimensionality, utilizing vectorized operations and memory-efficient filtering.
* **Feature Engineering:** Developed a custom base_price variable (price / surge_multiplier) to normalize platform-specific surge mechanics, enabling a fair comparison between Uber’s hidden surge and Lyft’s transparent multipliers.
* **Disparity Analysis:** Quantified and deconstructed a 9.8% average Lyft-Uber price gap, proving it was primarily driven by ride-type composition (Lux-WAV mismatch) rather than geography or distance.

### 2. Statistical Modeling & Predictive Analytics
* **Stratified Regressions:** Engineered cab-type-stratified models with interaction terms (distance * cab_type) to capture distinct per-mile rates, achieving an R² of 0.951.
* **Lasso Feature Selection:** Implemented Lasso regularization to prune non-contributing temporal and weather variables, identifying distance and product tier as the primary structural drivers.
* **Surge Predictability:** Demonstrated that Lyft’s explicit surge increases price predictability (R² shift from 0.48 to 0.82) compared to Uber’s opaque pricing strategy.

### 3. Market Segmentation (K-Means Clustering)
* **Optimal K-Selection:** Applied the Elbow Method to identify 4 distinct market clusters based on distance, base price, surge, and time of day.
* **Segment Discovery:**
    * **Commuter Pools:** High-volume, short trips around Haymarket Square (Clusters 1 & 4).
    * **Premium Corridors:** High-surge, business-oriented trips (e.g., Back Bay to North Station) dominated by Lux Black services (Cluster 2).
    * **Institutional/High-Value:** Medium-long trips (e.g., BU to Financial District) where revenue is driven by distance rather than surge (Cluster 3).

### 4. Efficient Computing & Parallelization
* **Parallel Execution:** Optimized model fitting by parallelizing five major regression models across multiple CPU cores, reducing total runtime to the duration of the single slowest model.
* **Sampling Workflows:** Implemented a 2% (10k observation) rapid-testing pipeline to validate code and preliminary results before execution on the full dataset.

## Core Technologies
* **Language:** R
* **Libraries:** K-Means (Unsupervised Learning), Linear & Lasso Regression, Parallel Core Processing
* **Domain:** Statistical Modeling, Big Data Analytics, Quantitative Engineering
