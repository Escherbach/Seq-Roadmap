# Appendix A - Platform Requirements

The metagenomic sequencing approach described in this document relies in the direct or indirect sequencing of viral material. Acquired sequence data may be processed in a number of ways. As a baseline, we will need to be able to detect known viruses. This is most commonly performed through alignment of reads to a reference of known viruses.

In order to assess the read length and accuracy requirements of our sequencing platform we simulated SARS-CoV-2 reads of varying lengths and accuracy. These reads were then aligned to the complete human genome, all NCBI Viruses, and the SARS-CoV-2 reference.

The figure below shows the percentage of reads that correctly aligned to the SARS-CoV-2 reference.

This plot suggests that **the majority of simulated reads are alignable at 20 bp, with an error rate as high at 5%.**

<img src="https://lh6.googleusercontent.com/_gt7HtPp-hr1pLQ5G2EOB8c5iKvB2T0hdnOiX5uQu2nZ0QKMJ213-B0lMKNBnm16OhbUrh1Jm2Efui_ZuAVSbYVePCOBqVepE5Xu4eP10i_0JfUU65JNo9IA0EUbsJkAuuzHLQQ62iQl7tmS6z6MD6c" alt="img" style="zoom:25%;" />

We can also simulate human reads of this length and error rate, then align them back to the human genome and SARS-CoV-2. If errored human material were to align to the SARS-CoV-2 reference this could result in a false positive. In this simulation, however, we have not been able to generate any such reads (after generating 100,000 reads).

Using this data, we can calculate the false negative and positive rates from these simulated reads. These compare favorably to known rates for qPCR:

|                     | qPCR | 20bp, 5% error |
|---------------------|------|----------------|
| False Negative Rate | 1%   | 0.01%          |
| False Positive Rate | 1.1% | 0%             |
