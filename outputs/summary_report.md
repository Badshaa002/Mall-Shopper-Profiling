# Mall Customer Segmentation: Executive Summary

## Retail business objective

Nexus Malls / Phoenix Marketcity needs a practical way to turn broad customer behaviour into targeted retail decisions. This project segments customers using annual income and spending score, allowing operations teams to plan tenant mixes, promotions, loyalty benefits, and physical layouts around meaningful shopper needs. The objective is to direct the right offer, experience, and zone to the right customer at the right moment.

## Feature-space review

Two feature spaces were evaluated. The primary two-dimensional space used Annual Income and Spending Score, the clearest behavioural canvas for commercial segmentation. A broader matrix added Age and encoded Gender; it supplied useful descriptive context but reduced group clarity under Euclidean distance. The 2D K-Means solution achieved a silhouette score of approximately 0.555, while the expanded feature set scored approximately 0.314. Age and gender should therefore inform persona messaging and reporting, rather than determine the first production cluster assignment.

## Model decision

K-Means with five clusters is recommended for deployment. It assigns every customer to an actionable segment, produces compact and well-separated groups, and remains stable when rerun with different initial seeds. Ward agglomerative clustering reached almost the same quality, validating that the pattern is real, but K-Means is easier to apply repeatedly to new shoppers. DBSCAN produced strong scores for dense core points; however, it classified roughly one quarter of customers as noise. That makes DBSCAN valuable for monitoring transitional customers, not as the main operational engine.

## Shopper personas

Big Spenders combine high income with high spending and merit premium-brand access, concierge experiences, and luxury pop-ups. Young Aspirers have lower income but high spending, making trend-led events, instalments, and attainable premium offers relevant. Careful Spenders sit in the middle on both income and spending and respond to dependable value, family bundles, and cross-store recommendations. Budget Shoppers have low income and low spending, so entrance-adjacent value stores, BOGO campaigns, and mobile coupons are appropriate. Mature Savers have high income but low spending; personalised quality, wellness, home, and service propositions are more compelling than blanket discounts.

## Future-proofing roadmap

The next phase should implement a real-time API tagging engine connected to the mall mobile app. The app can submit income and spending proxies, then receive a persona tag and relevant offer in milliseconds through the saved scaler and K-Means model. Add app footfall paths, Wi-Fi dwell time, transaction categories, basket values, visit frequency, parking activity, and campaign response to continuously enrich the model. A governed monitoring layer should track drift, conversion by persona, fairness, and model quality, while scheduled retraining keeps segmentation aligned with changing shopper behaviour.
