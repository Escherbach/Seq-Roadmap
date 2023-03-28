# A roadmap towards ubiquitous metagenomic sequencing

COVID-19 has clearly demonstrated that our ability to detect and contain new pathogens capable of causing a pandemic are not up to the task. This is all the more worrying since we can be confident that SARS-CoV-2 is far from the worst pathogen we could face within our lifetimes. There is therefore a pressing need for technological solutions to enable fast detection of new pathogens and their early containment with rapidly available mass testing.

Metagenomic sequencing (MGS) was previously identified as a technology that could accomplish this goal. However, in COVID-19, we have seen that sequencing has had a limited relative to its huge potential: while it has aided initial sequence identification and variant tracking, a number of bottlenecks prevent its widespread adoption at the point of need.

In this report, we look at these bottlenecks and attempt a first-principles analysis of what it would take to make technology for metagenomic sequencing truly ubiquitous, fit for developed and low-income countries alike. Given the urgency of the issue, we look for solutions involving low technical risk and are can substantially enable our preparedness for potential new pandemics in a 5-year timeframe.

|                           | Current state<br />[Chapter 1](./ch/current-state)           | Target<br />[Chapter 2](./ch/target)                         | Realistic approaches (5-10y)<br />[Chapter 3](./ch/roadmap)  |
| ------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Pandemic preparedness** | World vulnerable to novel pathogens; majority of infectious disease undiagnosed. | Routine pathogen-agnostic testing for severe respirarory disease. | Metagenomic sequencing widespread in the clinic and point of need. |
| **Sequencing technology** | ~30,000 sequencers, mostly in centralized laboratories.      | Millions of devices at the point of need.                    | Integrated low-cost sample-to-answer devices.                |
| **Sample preparation**    | Complex workflows, lack of standardization, contamination issues. | Low-cost automated qPCR-style sample preparation             | Standardized injection-molded reagent cartridges.            |
| **Sequencing platforms**  | - Cost of goods >$100. <br />- Pooling necessary<br />- Time to answer >24h. | - COG <<$10<br />- single sample analysis<br />- <1h to answer. | Low-cost mass-produced nanopore and/or single-molecule optical sequencers. |




![compressed-timeline](https://user-images.githubusercontent.com/106965942/226424152-81c794be-19a9-40f8-826e-1c7dc76eb8a7.png)



> Ubiquitous metagenomic sequencing could dramatically compress the timeline to detection of a new pathogen and at the same time provide an immediate mass testing capacity

## Current State

### qPCR tests are the gold standard
Limit of detection.
Sample-to-answer workflows.
Cost.
Time to answer. qPCR dominates the majority of current sequencing approaches in terms of time to answer. While nanopore sequencers can achieve a sequencing run of less than an hour, complex sample prep and pooling necessitated by high single sample costs imply a much longer de facto sample-to-answer time.

### MGS has not yet been adopted as a diagnostic

### Sequencing technologies have been optimized for accuracy, read length and cost per base
<img width="1000" alt="seqapproaches" src="https://user-images.githubusercontent.com/106965942/226617729-c9743f37-c873-422d-abbd-6f0ea8af98dd.png">


Next-generation sequencing platforms are currently offered by a range of players: Illumina, MGI, Oxford Nanopore, Pacific Biosciences, SeqLL, GenoMind, Qitan Technology and Thermo (Ion Torrent). A number of other players are also poised to enter the market (Element Biosciences, Singular Genomics, Ultima Genomics). For the most part, however, these players use expired Illlumina intellectual property. Approaches in this category therefore in most cases have similar cost-of-goods-sold (COGS) and performance characteristics as Illumina, and we will not address them here separately.

In terms of run time, only Oxford Nanopore and Pacific Biosciences platforms currently provide results within an hour (required to provide results within an ambulatory care visit, and comparable to current qPCR platforms).

### There were about 30,000 sequencers in the world in 2022

![img](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F04ac909d-664e-4ba7-8027-eddef4ae3d6c_671x465.png)


### High cost per sample necessitates sample pooling

```mermaid
graph LR
A[High cost per sample] --> B[Multiplexing]
B --> C[Slow turnaround time]
B --> D[Low sensitivity]
```

The cheapest runs of Illumina instruments currently cost \~\$300 to \$500[⁹](https://www.zotero.org/google-docs/?NJMTcC). To our knowledge, the cheapest run (Oxford Nanopore’s Flongle) costs closer to $100[¹⁰]. Even at this price point, healthcare providers are unlikely to use these instruments for sequencing single samples.

Batching and **multiplexing** multiple samples for a single sequencing run can significantly reduce the cost per sample, but introduces a delay before sequencing can begin. The delay is dependent on the nature of the testing facility and the number of samples being received per day, but typically, this is on the order of a week. This **delay of days to weeks** is likely unacceptable in an infectious disease diagnostic context where we ideally want to provide results as rapidly as possible.

Another downside of multiplexing onto a single chip is the significant reduction in sensitivity of the test, since the sequence coverage per sample reduces proportional to the number of samples.

Therefore, the high single-run cost for current instruments makes them a poor fit for diagnostic applications. This is the case even if we look at the COGS (Illumina \$50 to \$100s, Oxford Nanopore \$50 to \$450 based on stated margins^([1](https://www.zotero.org/google-docs/?uZfJ69) [12](https://www.zotero.org/google-docs/?tljpmF)). Cheaper options could make running single-sample tests economically viable.

### Complex worfklows limit use to specialized labs

Sequencing-based assays are complex and typically require multiple hours of skilled labor to execute (both in the wet lab and data analysis).

A pushbutton “sample-to-answer” sequencing platform could allow minimally-trained personnel to load a sample and walk away from the device. Such a platform could have a major impact on the ease of implementation of sequencing-based diagnostics. Yet, no sample-to-answer sequencing platform currently exists.

Efforts have been made to automate parts of the sample preparation and library preparation process workflows, but these have largely addressed research applications or users who are comfortable investing effort in developing automation systems to process large numbers of samples in centralized labs. No low-cost fixed protocol suitable for use in a clinical context is available.

### Long time to answer disqualifies sequencing in for infectious disease diagnosis

We previously discussed how the requirement of multiplexing can increase diagnostic turnaround time by days to weeks. Sending samples to a centralized lab followed by the execution of complex workflows by trained personnel also adds significantly to the time to answer. Indeed, current metagenomic-based pathogen tests often have a turnaround time of more than two weeks [¹³](https://www.zotero.org/google-docs/?7jVZxG).

On the sequencing technology front, Illumina’s runs typically fall between 24-48 hours, while their fastest runs are \~4 hours[¹⁴](https://www.zotero.org/google-docs/?RCkl9s),. While this may be sufficient for some use cases, it is hard to see how a truly ubiquitous technology base could be built on this base. However, nanopore and single-molecule approaches can currently provide sequencing data in a \<1-hour timeframe.

[Sample and library preparation](https://sequencing-roadmap.org/sample-prep) are also significant bottlenecks here. This is strongly dependent on the sequencing technology being used but tandard protocols typically take more than 2 hours. In later sections, we discuss approaches which can provide sequencing-ready DNA in \~10 minutes[¹⁵](https://www.zotero.org/google-docs/?gUoxVG).


## Target
### Pandemic-proof seqeuncers should be evaluated on sensitivity, cost and time to answer
In this section, we evaluate the current landscape of sequencing platforms against the technical requirements we have previously established:

1. Platforms should process single samples.
2. Time to answer should be less than 1 hour.
3. The COGS should be comparable to qPCR (<$10).
4. Sensitivity should be comparable to qPCR.


### qPCR-level sensitivity implies modest requirements for a sequencing platform

What does the requreirement of qPCR-level sensitivity imply for actual sequencing instrumentation? Below, we attempt to answer this question for the baseline task of detecting known viruses. Acquired sequence data may be processed in a number of ways, most commonly through alignment of reads to a reference of known viruses.

In order to assess the read length and accuracy requirements of our sequencing platform we simulated SARS-CoV-2 reads of varying lengths and accuracy. These reads were then aligned to the complete human genome, all NCBI Viruses, and the SARS-CoV-2 reference. The figure below shows the percentage of reads that correctly aligned to the SARS-CoV-2 reference. This plot suggests that **the majority of simulated reads are alignable at 20 bp, with an error rate as high at 5%.**

<img src="https://lh6.googleusercontent.com/_gt7HtPp-hr1pLQ5G2EOB8c5iKvB2T0hdnOiX5uQu2nZ0QKMJ213-B0lMKNBnm16OhbUrh1Jm2Efui_ZuAVSbYVePCOBqVepE5Xu4eP10i_0JfUU65JNo9IA0EUbsJkAuuzHLQQ62iQl7tmS6z6MD6c" alt="img" style="zoom:25%;" />

We can also simulate human reads of this length and error rate, then align them back to the human genome and SARS-CoV-2. If errored human material were to align to the SARS-CoV-2 reference, this could result in a false positive. In this simulation, however, we have not been able to generate any such reads (after generating 100,000 reads).

Using this data, we can calculate the false negative and positive rates from these simulated reads. These compare favorably to known rates for qPCR:

|                     | qPCR | 20bp, 5% error |
|---------------------|------|----------------|
| False Negative Rate | 1%   | 0.01%          |
| False Positive Rate | 1.1% | 0%             |

While we would ideally seek to exceed these specifications, building a platform which fits all our requirements requires compromise. In the next section we shall see that current instrumentation has been designed around the requirements of different applications and is a poor fit for point-of-care diagnostics.

## How to Get There
