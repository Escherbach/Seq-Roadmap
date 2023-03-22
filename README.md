# A roadmap towards ubiquitous metagenomic sequencing

Metagenomic sequencing (MGS) has the potential to [transform clinical diagnosis](https://www.nature.com/articles/s41576-019-0113-7) of infectious disease and [our ability to detect emerging pandemics](https://blogs.scientificamerican.com/observations/how-to-snuff-out-the-next-pandemic/).

In this roadmap, we work backward from the vision of ubiquitous metagenomic sequencing at the point-of-care as a means of compressing the time required to detect outbreaks of novel pathogens from weeks to months.



![compressed-timeline](https://user-images.githubusercontent.com/106965942/226424152-81c794be-19a9-40f8-826e-1c7dc76eb8a7.png)

- As of early 2023, MGS is not used widely used at the point of care. The reasons for this status quo can be divided into two categories: (a) lack of **clinical validation** and (b) lack of **incentive for adoption** due to high cost, complex workflows and long turnaround times.
- Clinical validation in terms of **sensitivity, specificity and impact on treatment** will be necessary to enable adoption at the clinic. In this report we review the literature assessing the use of MGS on clinical samples and quantitatively model clinical sensitivity of MGS under different assumptions. We conclude that **sensitivity can be comparable to that of qPCR** given sufficient sequencing depth. See [chapter on sensitivity and platform requirements](http://sequencing-roadmap.org/sensitivity).
- In the context of infectious disease testing, **time to answer**, **simplicity of sample preparation** and **cost** are essential. Currently available sequencing technologies have largely been optimized for a different set of criteria. In particular, the most widespread approach of Illumina-style sequencing by synthesis is unlikely to provide sufficient sequencing depth if we are aiming for a sample-to-answer time of ~1 hour. We see **two candidate technologies** that could provide sufficient sequencing depth in this timeframe at a cost comparable with qPCR. These are **nanopore sequencing** and **single-molecule optical sequencing**. See discussion of [platforms](https://escherbach.github.io/seq-roadmap/platforms).
- For clinical viability, any platform will need to be integrated into a dramatically simplified sample-to-answer system. While the exact design of these devices will have to be adapted for particular platform of choice, we conclude design of a simple, low-cost sample prep cartridge can be quite straightforwardly adapted from qPCR sample-to-answer systems. See chapter on [sample preparation](http://sequencing-roadmap.org/sample-prep).

## Chapters

1. [Clinical MGS and Early Detection](http://sequencing-roadmap.org/early-detection)
2. [Sensitivity and Platform Requirements](http://sequencing-roadmap.org/sensitivity)
3. [Sample Preparation](http://sequencing-roadmap.org/sample-prep)
4. [Sequencing Platforms](http://sequencing-roadmap.org/platforms)
5. Conclusions and Recommendations
