# Ranking and Algorithms

## Collection Search Bar Results

The search bar at stargaze.zone employs a dynamic algorithm to rank collections based on recent market activity and liquidity metrics. This ranking system helps users discover popular and emerging NFTs by highlighting collections gaining traction. It's designed to surface collections that are growing in interest, ensuring that users can find NFTs that are trending upward across various price points.

### How it Works

1. **Data Collection**: We gather recent data on NFT sales, listings, and active offers.
2. **Filtering**: Collections meeting minimum activity criteria are considered for ranking.
3. **Metric Calculation**: Key performance indicators are calculated over various time frames (30 days, 7 days, 1 day, and 6 hours), including:
   * Sales volume
   * Unique buyers
   * Volume growth rates
   * Buyer interest indicators
4. **Normalization**: Metrics are scaled to ensure fair comparisons across all collections.
5. **Scoring**: Collections receive scores for each time frame based on weighted metrics.
6. **Final Ranking**: A composite score is calculated to rank collections, balancing long-term performance with recent trends.

