# Technical requirements and Bottlenecks in current approaches

In the [previous section](early-detection), we have laid out the need for ubiquitous metagenomic sequencing at the point of care. In this chapter, we focus on the concrete requirements

It is of note that a number of sequencing-based diagnostic approaches have been attempted during COVID-19. However, they have largely failed to gain traction and cumulatively represented \<1% of the testing used to detect and monitor COVID-19 infections[⁸](https://www.zotero.org/google-docs/?mhRwMO):

There are a number of reasons for this which we summarize in the table below:

|                      | qPCR            | Metagenomic Sequencing |
| -------------------- | --------------- | ---------------------- |
| Cost-of-goods (COGs) | \$1 to \$5      | > \$100                |
| Automation           | Widely deployed | Limited                |
| Time to answer       | \< 1 hour       | Days to Weeks          |

Unless these issues are addressed, metagenomic sequencing-based approaches are unlikely to gain widespread adoption.

### High cost per sample necessitates multiplexing

```
graph LR
A[High cost per sample] --> B[Multiplexing]
B --> C[Slow turnaround time]
A --> D[Low sensitivity]
```
The cheapest runs of Illumina instruments currently cost \~\$300 to \$500[⁹](https://www.zotero.org/google-docs/?NJMTcC). To our knowledge, the cheapest run (Oxford Nanopore’s Flongle) costs closer to $100[¹⁰]. Even at this price point, healthcare providers are unlikely to use these instruments for sequencing single samples.

Batching and **multiplexing** multiple samples for a single sequencing run can significantly reduce the cost per sample, but introduces a delay before sequencing can begin. The delay is dependent on the nature of the testing facility and the number of samples being received per day, but typically, this is on the order of a week. This **delay of days to weeks** is likely unacceptable in an infectious disease diagnostic context where we ideally want to provide results as rapidly as possible.

Another downside of multiplexing onto a single chip is the significant reduction in sensitivity of the test, since the sequence coverage per sample reduces proportional to the number of samples.

Therefore, the high single-run cost for current instruments makes them a poor fit for diagnostic applications. This is the case even if we look at the COGS (Illumina \$50 to \$100s, Oxford Nanopore \$50 to \$450 based on stated margins^([1](https://www.zotero.org/google-docs/?uZfJ69) [12](https://www.zotero.org/google-docs/?tljpmF)). Cheaper options could make running single-sample tests economically viable.

### Automation

Sequencing-based assays are complex and typically require multiple hours of skilled labor to execute (both in the wet lab and data analysis).

A pushbutton “sample-to-answer” sequencing platform could allow minimally-trained personnel to load a sample and walk away from the device. Such a platform could have a major impact on the ease of implementation of sequencing-based diagnostics. Yet, no sample-to-answer sequencing platform currently exists.

Efforts have been made to automate parts of the sample preparation and library preparation process workflows, but these have largely addressed research applications or users who are comfortable investing effort in developing automation systems to process large numbers of samples in centralized labs. No low-cost fixed protocol suitable for use in a clinical context is available.

### Time to Answer

We previously discussed how the requirement of multiplexing can increase diagnostic turnaround time by days to weeks. Sending samples to a centralized lab followed by the execution of complex workflows by trained personnel also adds significantly to the time to answer. Indeed, current metagenomic-based pathogen tests often have a 2-4 week turnaround time[¹³](https://www.zotero.org/google-docs/?7jVZxG).

On the sequencing technology front, Illumina’s fastest sequencing runs are \~4 hours[¹⁴](https://www.zotero.org/google-docs/?RCkl9s), though their runs typically fall between 24-48 hours. In combination with the factors discussed above, we believe this is too slow to provide valuable clinical feedback to patients in many cases. However, nanopore and single-molecule approaches can currently provide sequencing data in a \<1-hour timeframe.

[Sample and library preparation](https://sequencing-roadmap.org/sample-prep) are also significant bottlenecks here. This is strongly dependent on the sequencing technology being used. Standard protocols typically take \>2 hours. In later sections, we discuss approaches which can provide sequencing-ready DNA in \~10 minutes[¹⁵](https://www.zotero.org/google-docs/?gUoxVG).
