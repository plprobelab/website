---
title: cid.contact
plotly: true
---

# `cid.contact`

This page shows performance metrics for the [cid.contact](https://cid.contact)
InterPlanetary Network Indexer. We gathered the data with our
[Tiros](/tools/tiros) measurement tool.

## Trends

{{< plotly json="../../plots/latest/ipni-trend-latencies-cid.contact.json" height="300px" >}}

The graph shows different percentiles of the "Time To First Provider Record" (TTFPR)
metrics over time. To measure the TTFPR, we start the stopwatch right before we
do the `https://{ipni}/cid/{cid}` HTTP request to the indexer and stop it when we have received and parsed
the full record.

In the above graph we aggregate these latency measurements on a daily basis and
calculate the 50th and 90th percentiles incorporating data from multiple
regions. In our measurement setup, we do multiple requests for the same CID. To
differentiate between cached and uncached latencies, we show the latencies of the
first requests for a CID as "uncached" and subsequent request latencies as
"cached".

It is important to note that the resulting TTFPR percentiles are artificial composites
and do not reflect the specific performance of any individual region. Rather,
it allows to discern general tendencies and fluctuations in TTFPR across the
combined dataset. By focusing on these overall trends, we can gain valuable
insights into the performance of IPNI TTFPR performance as a whole, making it easier to
identify any notable deviations or improvements in that metric over time.

## Lookup Latencies

The graphs presented below display the latencies for the "Time To First Provider
Record" (TTFPR) observed from various regions over the past few days. Each line
represents the Cumulative Distribution Function (CDF) of the lookup latency in a
specific region. Note that the x-axis is presented in a
logarithmic scale. We distinguish between two types of latencies: uncached,
which refers to the first request for a CID, and cached, which pertains to
subsequent requests for a CID.

### Uncached

{{< plotly json="../../plots/latest/ipni-snapshot-uncached-latencies-cdf-cid.contact.json" height="300px" >}}

### Cached

{{< plotly json="../../plots/latest/ipni-snapshot-cached-latencies-cdf-cid.contact.json" height="300px" >}}

### DHT Comparison

{{< plotly json="../../plots/latest/ipni-snapshot-dht-comparison-cid.contact-p90.json" height="300px" >}}

The bar chart above illustrates the 90th percentile of latency associated with
looking up a provider record using two different methods: the Distributed Hash
Table (DHT) and this network indexer.

The network indexer's lookup latencies are divided into two categories: uncached and cached latencies. 
When a CID is looked up for the first time, the response is cached at the edge. The "uncached" latency
bars indicate the latencies for initial CID lookups, while the "cached" latency bars represent the latencies for subsequent lookups.
