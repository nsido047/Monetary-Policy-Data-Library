# Monetary-Policy-Data-Library
This repository contains the code and documentation for the **Monetary Policy Data Library**, which compiles time series data on key monetary policy variables across numerous central banks and countries. Researchers in international finance, monetary economics, and political economy often lack centralized access to structured and cleaned data on global central bank policy decisions, balance sheet operations, and unconventional monetary tools. This project proposes the creation of a dedicated digital library designed to consolidate, standardize, and document publicly available but currently fragmented—data on historical decisions, balance sheets, policy operations, and forward guidance from major central banks. The platform aims to serve as a research-grade infrastructure layer that simplifies empirical work on monetary policy, while promoting accessibility and transparency in global macroeconomic research.

# Addressing The Problem
Over the past two decades, central bank operations and transparency have undergone a dramatic transformation, particularly in terms of publicly available data and the tools used to conduct monetary policy. The 21st-century adoption of additional policy tools such as quantitative easing (QE), forward guidance, and yield curve control (YCC) has spurred a surge in academic research within monetary economics. This growth in scholarship has, in turn, created greater demand for structured, comparable datasets to support empirical analysis. Yet, obtaining clean and harmonized data across central banks remains challenging. **The problem is twofold:** first, data are often siloed within the individual repositories of each central bank or other sources such as the Bank of International Settlements (BIS), International Monetary Fund (IMF) or other data aggreators, with only limited attempts at consolidation; second, there is little consensus in event studies on which policy decisions or statements merit inclusion, leading to inconsistent datasets—such as mismatched timelines for QE announcements—across research papers _(see, for example, Lyonnet and Werner, 2012; Rosa, 2014; Filippo et al., 2022)_. Determining whether a given statement is likely to have a material and unexpected impact on markets is often subjective, and the lack of standardization forces researchers to compile event timelines and macro-financial datasets manually, drawing from PDF releases, institutional websites, or proprietary aggregators. The Monetary Policy Library addresses this gap by providing a curated, open-access repository of clean, structured, and comparable monetary policy data, designed specifically to support rigorous and reproducible research. 

Furthermore, the creation of such a data library would assist researchers in compiling information for cross-country monetary policy studies. There is significant value in being able to quickly access a complete dataset of QE announcements—along with their associated details—made by the U.S. Federal Reserve (Fed) since the Global Financial Crisis, without the need to manually trace each announcement from official communications on its website. This dataset could then be directly compared to similar collections from the Bank of England (BoE) or the European Central Bank (ECB) within the same structured framework. Several empirical event studies examining the impact of QE on asset prices have developed sets of policy announcements and their associated market effects, drawing either from prior research or their own compilations. The table below, for example, presents changes in interest rates for each date in the baseline event set, as well as for dates when the FOMC issued communications about LSAPs that conveyed little new information. 

**Example of An Federal Reserve Announcement Dataset From _Remache et al., 2011, p. 19_**

| Date       | Event                                 | 2y UST | 10y UST | 10y Agy | Agy MBS | 10y TP | 10y Swap | Baa Index |
|------------|---------------------------------------|--------|---------|---------|----------|--------|----------|-----------|
| 11/25/2008 | Initial LSAP Announcement             | -2     | -22     | -58     | -44      | -17    | -29      | -18       |
| 12/1/2008  | Chairman Speech                        | -8     | -19     | -39     | -15      | -17    | -17      | -12       |
| 12/16/2008 | FOMC Statement                        | -9     | -26     | -29     | -37      | -12    | -32      | -11       |
| 1/28/2009 | FOMC Statement                         | 10     | 14      | 14      | 11       | 9      | 14       | 2         |
| 3/18/2009 | FOMC Statement                         | -22    | -47     | -52     | -31     | -40    | -39      | -29       |
| 4/29/2009  | FOMC Statement                         | 1      | 10      | -1      | 6        | 6      | 8        | 3         |
| 6/24/2009 | FOMC Statement                         | 10     | 6       | 4       | 4        | 4      | 6        | 5         |
| 8/12/2009 | FOMC Statement                         | -2     | 5       | 4       | 2        | 4      | 3        | 2         |
| 9/23/2009 | FOMC Statement                         | 1      | -3      | -1      | -1       | -5     | -5       | -4        |

By consolidating fragmented sources into a standardized, open-access repository, the Monetary Policy Library removes a major barrier to conducting timely, accurate, and comparable monetary policy research. Instead of spending days or weeks reconstructing event timelines from disparate documents, researchers can directly access clean datasets that are ready for empirical analysis and have been compiled through prior peer-reviewed research and publicly available Government data. This not only improves research efficiency, but also enhances reproducibility and cross-country comparability in monetary economics. In the following sections, we demonstrate how this approach works in practice and how it can be applied to real-world policy event studies.

# Scope and Initial Dataset: Quantiative Easing Announcements

To begin building the Monetary Policy Data Library, I focus initially on compiling a comprehensive, structured dataset of QE announcements from four major central banks. QE events are a pivotal unconventional monetary policy tool that have been widely studied over the past two decades, making them an ideal starting point due to their empirical relevance and well-documented history. Focusing on QE announcements rather than the implementation of asset purchases captures the key moments when market participants update their expectations based on new information. Announcements provide clear, discrete events that are easier to timestamp and analyze, reflecting the central bank’s policy intentions and signaling effects, which drive the immediate financial market reactions.

### Central Banks Covered  
The initial scope covers QE announcements from the following central banks who have conducted large scale asset purchase programs since the modern use of the tool by the Bank of Japan in 2001:

- U.S. Federal Reserve (Fed) — starting from the Global Financial Crisis period (2008) to present  
- European Central Bank (ECB)  
- Bank of England (BoE)  
- Bank of Japan (BoJ)  

### Data Elements Collected  
For each QE announcement, I aim to collect:

- Announcement date and time  
- Type of QE program (e.g., asset purchases, balance sheet expansion)  
- Size and scale of asset purchases (if disclosed)  
- Specific asset classes targeted (e.g., Treasury securities, mortgage-backed securities)  
- Associated policy statements or forward guidance text  
- Market reactions on announcement day (e.g., changes in treasury yields, swap rates) where available  

### Data Sources  
- Official central bank websites and press releases  
- Monetary policy statements and meeting minutes  
- Peer-reviewed event study literature for validated announcement dates (e.g., Remache et al., 2011)  
- Financial market data providers for associated market impact variables  

### Importance of Starting with QE Announcements  
Starting with QE announcements provides a clearly defined event type that is central to recent monetary policy research. Standardizing this dataset enables rigorous cross-country and temporal comparisons, facilitating analysis of the transmission and effectiveness of unconventional policy tools. Furthermore, unlike interest rate decisions, which generally occur on predetermined schedule and a complete history already readilyt available, QE announcements are more ambiguous, occurring irregularly and sporadically, making it more challenging to compile a complete and consistent dataset increasing the novelty of such a complete set.

# Methodology

# References
Busetto, F., Chavaz, M., Froemel, M., Joyce, M., Kaminska, I., & Worlidge, J. (2022). QE at the Bank of England: A Perspective on its Functioning and Effectiveness (Volume 2022, Issue Q1). Bank of England. https://www.bankofengland.co.uk/quarterly-bulletin/2022/2022-q1/qe-at-the-bank-of-england-a-perspective-on-its-functioning-and-effectiveness

Lyonnet, V., & Werner, R. (2012). Lessons from the Bank of England on ‘quantitative easing’ and other ‘unconventional’ monetary policies. International Review of Financial Analysis, 25, 94–105. https://doi.org/10.1016/j.irfa.2012.08.001

Remache, J., Gagnon, J., Sack, B., & Raskin, M. (2011). The Financial Market Effects of the Federal Reserve’s Large-Scale Asset Purchases *. EliScholar. https://elischolar.library.yale.edu/cgi/viewcontent.cgi?article=2214&context=ypfs-documents

Rosa, C. (2012). How “Unconventional” are Large-Scale Asset Purchases? The Impact of Monetary Policy on Asset Prices. Federal Reserve Bank of New York Staff Reports. https://www.newyorkfed.org/research/staff_reports/sr560.html
