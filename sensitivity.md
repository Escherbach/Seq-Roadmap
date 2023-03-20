# Sensitivity
## Comparing qPCR and Sequencing

qPCR is widely believed to be the “gold standard” in molecular diagnostic testing. qPCR has a very low  limit of detection (LoD). In some cases, a handful of copies can be detected in a sample. This is generally assessed using synthetic material spiked into a sample to create standard curves like the following:

![](https://lh3.googleusercontent.com/45LCmGVIxaMMDK7f8jl2RiZNuIVEIuEclahtz6uLr3JEwCMaTThtwrw22ncYAjGE1Pr8hiHy2y_hM6zQozDO9BG_vlKGpmbrbq9xuh7tYmeQzkWmCDMMKSKE3rtWpskeMjY4YgE30T1fT30Oyrv2W4Y)

Because qPCR targets a primer-delimited region (the amplification region), it is **insensitive to background material**. A high fraction of human material (mostly rRNA in the case of RT-qPCR) or bacterial material will have only a minor effect on the sensitivity of qPCR. In other words, the LoD relies on the sample's **absolute abundance of the target**. 

**Metagenomic sequencing**, however, is **sensitive to background material**. To ensure that your target(s) of interest is detected, you must also sequence through background fragments until your target is reached. Thus, metagenomic’s LoD relies on the relative abundance of the target among the other nucleic acid in the sample.

Here, we review the literature on the sensitivity of MGS in the context of human clinical samples. This literature demonstrates that not only does MGS have a broader scope of applications than qPCR, allowing the detection of known and unknown viruses[12](https://www.zotero.org/google-docs/?broken=jUvyc2), but that it also has at least comparable sensitivity when adequate read depth is used. Indeed, potential false negatives were detected by sequencing, indicating a greater test sensitivity in some cases. 

## Metagenomic Sequencing Studies

We reviewed 42 publications (Appendix D) where metagenomic sequencing was used on pathogenic samples. These were collected from literature searches, extracted from review papers, and received via a public call for relevant publications.

We then selected publications that met the following criteria:

-   More than 10 positive subjects.
    
-   More than 10M average reads per sample.
    
-   Did not use only contrived or pooled samples.
    
-   Was not a targeted or semi-targeted study.
    

This ensures that studies have a sufficiently large size and number and that samples have sufficient reads to assess the sensitivity of sequencing. The result was the following 8 papers:

![](https://lh6.googleusercontent.com/dbC9cBgpRMtVZbYGlGvO9fSZDJx3cBH3WOPsJXWuprzq2ydnI2WZVey-fbRxkPIZ4UhHMcFThCbrp2KjYHi_XHcOFi3F47XTYg0F-ah9-tO7fyE0s4wLn2KeZC9HVAyiD-sPDDT_kpvCde4llfsuwBk)

  Detailed comments on these publications can be found in Appendix E. Sensitivity was either calculated using data presented in the papers (based on agreement with qPCR, Panels, or Serology testing) or used explicit statements from these publications.

Where a sensitivity estimate could be calculated against qPCR (5/8 papers), it was >96%. This is the agreement we would expect to see between these tests, a sentiment broadly in agreement with the conclusions of these publications (see Appendix E).

Moreover, 4 of the 8 papers have explicit statements on qPCR false negatives stating that sequencing was able to identify likely false negatives from qPCR using sequencing (see Appendix E) and therefore showed the potential for increased sensitivity relative to qPCR.

## Contrasting qPCR and Sequencing

As discussed above, the LoD for qPCR is very low, and the approach is insensitive to background material. However, qPCR is limited to a single region of our target pathogen. In the case of a viral target, this is typically in approximately 100 bp. For SARS-CoV-2, this is 0.3% of the genome. In sequencing, any location on the genome provides information that can enable detection.

If all viral fragments are fully intact at the point of detection, this distinction is irrelevant. However, if the genome is fragmented, qPCR will only be able to detect that fraction of fragments that contain the amplification region. We show in Appendix H that studies suggest that SARS-CoV-2 (and other viral genomes) is likely fragmented either at collection or at point of analysis.

Moreover, because qPCR uses primer sequences to enable detection, mutations in the primer region will cause issues for qPCR (see Appendix H). While this has not been a significant issue during COVID-19, it is worth noting.

## Modeling qPCR and Sequencing

In order to more completely explore the specifications of a metagenomic sequencing based diagnostic we have created a simple model. In the first instance, we parameterize this model estimating our parameters from the JumpCode dataset mentioned in the review above: 

-   Total RNA: 10ng
    
-   Genome Size: 30Kb
    
-   rRNA fraction: 60%
    
-   qPCR Target Region: 90nt
    
-   Fragment Size: 1000nt
    
-   Read Count: 40M
    

The model then calculated the number of reads generated, and “on target fragments” which can be used to estimate CT values from standard curves.

![](https://lh6.googleusercontent.com/qjy568MhIsKtK70_KOFLLzolcjQAUHLD2a1wIQ1RDaXQVs3lyOHE0a5Z3hwMnhp-P_h8NcGiLt4BoheB3UfMAm7jx-cDDLiCfmpVsBE95OF1_CxVMOVikHnDOPL_oYRB-5v4mcwbpeCC1Ua4molgnvs)

The model suggests that using the inputs above, **we should expect to hit a Ct of 35 with sequencing**, which is also roughly the conclusion the JumpCode paper comes to.

With these parameters the model output is in reasonable agreement with the JumpCode dataset:

![](https://lh6.googleusercontent.com/n4vyC1rqYGc0McmkKkAmGRPCpCnrqgDVmekfS8h1WEWr4igQK89ZoVXKlBPwCwwT5ded4-cbmGqJdN8sIkZbPBrESEHXaiAPmRYm4KzYAQsCticL9MvBy9qTDc79ADpL5Ixs5XNAvhNxKBjqzKSECag)

While the model above shows the “expected number of reads” this is not the ideal metric for assessing a sequencing based diagnostic. As the distribution of read counts between samples will follow a Poisson distribution we are more interested in the probability of seeing “at least one read”. To maintain a < 1 in 1000 false negative rate this should be 0.999.

The plot below shows how “probability of signal read” varies with read count and target fraction. 

![](https://lh4.googleusercontent.com/V_2zvr8SkeYYrPlWU9q3sV5u3c5fiHHcoD7eFx8tpsx23JCYJDHVS6_5P77Duf3gwGFKt0KGK9Sqbhw5tksOS4gZenz6AGTAY1smbjW0jDd_NgfPhsiXFoGLxkq1IS_lRUdDLyXlwHxRW57DjVxV1aY)

  

We can use this plot to determine the approximate number of reads required for a given target fraction. For example to have a probability of seeing at least one read > 0.999 we will require > 3.5M reads without rRNA depletion.

Below we see the same plot with target fraction used to calculate expected CT values from a qPCR test assuming 10ng of total material (and parameters others similar to the simulation shown above):

  

![](https://lh4.googleusercontent.com/Cp_pOT9M-XlZKXdG4uzo6l3vzfK5ubauwzAMtLXIIuwJOAuukXWvvCUPKDL_NAr52syC3coTVcwnGmBUZJX36ZrJ7POuPox2uadYMB-bJQ073jP6yPJCJ-df2QSesSl922l7Qhj_yigMcqE0I88Ys2c)

  

We can see that 300K reads are sufficient to reach CT 30, 1M reads CT 33 etc.

  

Based on this analysis we believe that 1 to 10M reads is sufficient throughput for our metagenomic sequencing platform. It should be noted that this is not an average but a lower limit. As such platforms that exhibit significant sample to sample variability will be at a disadvantage.

**