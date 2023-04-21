# A roadmap towards ubiquitous metagenomic sequencing
The first COVID-19 infection occured in mid-October to mid-November of 2019, at least six weeks earlier than the Wuhan cluster of infections was identified in late December 2019.[^1] The SARS-CoV-2 genome was only made publicly available in January 2020, more than two months after the first human transmission.[^2] This delay resulted in millions of deaths and trillions of dollars in economic costs.

COVID-19 - far from the worst pandemic we could face within our lifetimes - has clearly demonstrated that our ability to detect and contain new pathogens capable of causing a pandemic are nowhere near where they should be. The diagnostic technologies we use for infections at the point of care are adapted to a small set of known pathogens and in princile incapable of recognizing the outbreak of an unsuspected or unknown pathogen.

There is therefore a pressing need for a universal diagnostic to enable fast detection of all pathogens and their early containment. We need an early warning system that can detect the emergence of a new pathogen in humans as early as possible, without any assumptions about what the pathogen might be. This system should also be able to characterize any pathogen in a human sample with sufficient information to triage the threat.

Such an early warning system would provide a one-to-one correspondence between a given sample and a patient so that health authorities can isolate that patient and perform contact tracing within hours of detecting the pathogen, in an attempt to contain its spread. Early detection and characterization would also allow for the rapid development and deployment of medical countermeasures and the activation of other emergency plans.

Such a device would allow the care provider to place a liquid sample from a patient in the device, then simply press a button and wait an hour for the list of all pathogens present in that sample. It would also allow for many samples to be run in parallel while still maintaining a one-to-one correspondence between the sample and the patient, so that each patient can be tested as they come through the clinic’s doors.

**Metagenomic sequencing (MGS)** was previously identified as a technology that could accomplish this goal. In this roadmap, we are exploring the vision of a device that performs fully-automated, end-to-end sample preparation and sequencing available at every hospital and care provider’s office throughout the world.

However, in COVID-19, we have seen that sequencing has had a limited relative to its huge potential: while it has aided initial sequence identification and variant tracking, a number of bottlenecks prevent its widespread adoption at the point of need. In this report, we analyze these bottlenecks and ask what it would take to **make the technology for metagenomic sequencing truly ubiquitous**, fit for developed and low-income countries alike in a 10-year timeframe.


|                           | Current state<br />[Chapter 1](./ch/current-state)           | Target<br />[Chapter 2](./ch/target)                         | Realistic approaches (5-10y)<br />[Chapter 3](./ch/roadmap)  |
| ------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Pandemic preparedness** | World vulnerable to novel pathogens; majority of infectious disease undiagnosed. | Routine pathogen-agnostic testing for severe respirarory disease. | Metagenomic sequencing widespread in the clinic and point of need. |
| **Sequencing technology** | ~30,000 sequencers, mostly in centralized laboratories.      | Millions of devices at the point of need.                    | Integrated low-cost sample-to-answer devices.                |
| **Sample preparation**    | Complex workflows, lack of standardization, contamination issues. | Low-cost automated qPCR-style sample preparation             | Standardized injection-molded reagent cartridges.            |
| **Sequencing platforms**  | - Cost of goods >$100. <br />- Pooling necessary<br />- Time to answer >24h. | - COG <<$10<br />- single sample analysis<br />- <1h to answer. | Low-cost mass-produced nanopore and/or single-molecule optical sequencers. |

## Requirements
What is it going to take to make metagenomic sequencing ubiquitous in clinics around the world? There are many aspects to the problem, including a complex regulatory landscape or changing the culture of diagnosis from hypothesis-driven to pathogen-agnostic. However, a necessary condition for these is the existence of an affordable, easy-to-use technical solution. In this report, we therefore focus on how to meet this first condition.

We specify the requirements as follows:
1. Platforms should process single samples.
2. Time to answer should be less than 1 hour.
3. The COGS should be comparable to qPCR (<$10).
4. Sensitivity should be comparable to qPCR.

### Matching the sensitivity of qPCR

qPCR is widely believed to be the “gold standard” in molecular diagnostic testing. qPCR has a very low  limit of detection (LoD). In some cases, a handful of copies can be detected in a sample. This is generally assessed using synthetic material spiked into a sample to create standard curves like the following:

![](https://lh3.googleusercontent.com/45LCmGVIxaMMDK7f8jl2RiZNuIVEIuEclahtz6uLr3JEwCMaTThtwrw22ncYAjGE1Pr8hiHy2y_hM6zQozDO9BG_vlKGpmbrbq9xuh7tYmeQzkWmCDMMKSKE3rtWpskeMjY4YgE30T1fT30Oyrv2W4Y)

Standard curve generated for N1 and N2 of SARS-CoV-2. Source: [Kudo et al. (2020)](https://www.researchgate.net/publication/342273491_Detection_of_SARS-CoV-2_RNA_by_multiplex_RT-qPCR)

Because qPCR targets a primer-delimited region (the amplification region), it is **insensitive to background material**. A high fraction of human material (mostly rRNA in the case of RT-qPCR) or bacterial material will have only a minor effect on the sensitivity of qPCR. In other words, the LoD relies on the sample's **absolute abundance of the target**. 

**Metagenomic sequencing**, however, is **sensitive to background material**. To ensure that your target(s) of interest is detected, you must also sequence through background fragments until your target is reached. Thus, metagenomic’s LoD relies on the relative abundance of the target among the other nucleic acid in the sample.

Here, we review the literature on the sensitivity of MGS in the context of human clinical samples. This literature demonstrates that not only does MGS have a broader scope of applications than qPCR, allowing the detection of known and unknown viruses, but that it also has at least comparable sensitivity when adequate read depth is used. Indeed, potential false negatives were detected by sequencing, indicating a greater test sensitivity in some cases. 

#### Empirical studies 

We reviewed 42 publications (Appendix D) where metagenomic sequencing was used on pathogenic samples. These were collected from literature searches, extracted from review papers, and received via a public call for relevant publications.

We then selected publications that met the following criteria:

-   More than 10 positive subjects.
-   More than 10M average reads per sample.
-   Did not use only contrived or pooled samples.    
-   Was not a targeted or semi-targeted study.
    

This ensures that studies have a sufficiently large size and number and that samples have sufficient reads to assess the sensitivity of sequencing. The result was the following 8 papers:

![](https://lh6.googleusercontent.com/dbC9cBgpRMtVZbYGlGvO9fSZDJx3cBH3WOPsJXWuprzq2ydnI2WZVey-fbRxkPIZ4UhHMcFThCbrp2KjYHi_XHcOFi3F47XTYg0F-ah9-tO7fyE0s4wLn2KeZC9HVAyiD-sPDDT_kpvCde4llfsuwBk)

Detailed comments on these publications can be found in Appendix E. Sensitivity was either calculated using data presented in the papers (based on agreement with qPCR, Panels, or Serology testing) or used explicit statements from these publications. Where a sensitivity estimate could be calculated against qPCR (5/8 papers), it was >96%. This is the agreement we would expect to see between these tests, a sentiment broadly in agreement with the conclusions of these publications (see Appendix E). Moreover, 4 of the 8 papers have explicit statements on qPCR false negatives stating that sequencing was able to identify likely false negatives from qPCR using sequencing (see Appendix E) and therefore showed the potential for increased sensitivity relative to qPCR.

### Resulting throughput requirements

As discussed above, the LoD for qPCR is very low, and the approach is insensitive to background material. However, qPCR is limited to a single region of our target pathogen. In the case of a viral target, this is typically approximately 100 bp. For SARS-CoV-2, this is 0.3% of the genome. In sequencing, any location on the genome provides information that can enable detection.

If all viral fragments are fully intact at the point of detection, this distinction is irrelevant. However, *if the genome is fragmented*, qPCR will only be able to detect that fraction of fragments that contain the amplification region. We show in Appendix H that studies suggest that SARS-CoV-2 (and other viral genomes) is likely fragmented either at collection or at point of analysis.

Moreover, because qPCR uses primer sequences to enable detection, mutations in the primer region will cause issues for qPCR (see Appendix H). While this has not been a significant issue during COVID-19, it is worth noting.

#### Model

In order to more completely explore the specifications of a metagenomic sequencing based diagnostic we have created a simple model. In the first instance, we parameterize this model estimating our parameters from the JumpCode dataset mentioned in the review above: 

-   **Total RNA:** 10ng
    
-   **Genome Size:** 30Kb
    
-   **rRNA fraction:** 60%
    
-   **qPCR Target Region:** 90nt
    
-   **Fragment Size:** 1000nt
    
-   **Read Count:** 40M


The model then calculated the number of reads generated, and “on target fragments” which can be used to estimate Ct values from standard curves.

![](https://lh6.googleusercontent.com/qjy568MhIsKtK70_KOFLLzolcjQAUHLD2a1wIQ1RDaXQVs3lyOHE0a5Z3hwMnhp-P_h8NcGiLt4BoheB3UfMAm7jx-cDDLiCfmpVsBE95OF1_CxVMOVikHnDOPL_oYRB-5v4mcwbpeCC1Ua4molgnvs)

The model suggests that using the inputs above, **we should expect to achieve a Ct of 35 with sequencing**, which is also roughly the conclusion the JumpCode paper comes to. The model output is in relatively close agreement with a dataset produced by Jumpcode:

<img src="https://lh6.googleusercontent.com/n4vyC1rqYGc0McmkKkAmGRPCpCnrqgDVmekfS8h1WEWr4igQK89ZoVXKlBPwCwwT5ded4-cbmGqJdN8sIkZbPBrESEHXaiAPmRYm4KzYAQsCticL9MvBy9qTDc79ADpL5Ixs5XNAvhNxKBjqzKSECag" style="zoom: 70%;" />

While the model above shows the “expected number of reads” this is not the ideal metric for assessing a sequencing based diagnostic. As the distribution of read counts between samples will follow a Poisson distribution we are more interested in the probability of seeing “at least one read”. To maintain a < 1 in 1000 false negative rate this should be 0.999.

We can determine the approximate number of reads required for a given target fraction. For example, to have a probability of seeing at least one read > 0.999 we will require > 3.5M reads without rRNA depletion. Below, we see the same plot with target fraction used to calculate expected Ct values from a qPCR test assuming 10ng of total material (and parameters others similar to the simulation shown above):  

<img src="https://lh4.googleusercontent.com/Cp_pOT9M-XlZKXdG4uzo6l3vzfK5ubauwzAMtLXIIuwJOAuukXWvvCUPKDL_NAr52syC3coTVcwnGmBUZJX36ZrJ7POuPox2uadYMB-bJQ073jP6yPJCJ-df2QSesSl922l7Qhj_yigMcqE0I88Ys2c" style="zoom:33%;" />

We can see that 300,000 reads are sufficient to reach a Ct of 30 and 1M reads correspond to a Ct of 33. Based on this analysis we believe that, as a lower limit, 1 to 10M reads is sufficient throughput for our metagenomic sequencing platform. Therefore, platforms that exhibit significant sample to sample variability will be at a disadvantage.

### Read length and accuracy requirements

What does the requreirement of qPCR-level sensitivity imply for actual sequencing instrumentation? Below, we attempt to answer this question for the baseline task of detecting known viruses. Acquired sequence data may be processed in a number of ways, most commonly through alignment of reads to a reference of known viruses.

In order to assess the read length and accuracy requirements of our sequencing platform we simulated SARS-CoV-2 reads of varying lengths and accuracy. These reads were then aligned to the complete human genome, all NCBI Viruses, and the SARS-CoV-2 reference. The figure below shows the percentage of reads that correctly aligned to the SARS-CoV-2 reference. This plot suggests that **the majority of simulated reads are alignable at 20 bp, with an error rate as high at 5%.**

<img src="https://lh6.googleusercontent.com/_gt7HtPp-hr1pLQ5G2EOB8c5iKvB2T0hdnOiX5uQu2nZ0QKMJ213-B0lMKNBnm16OhbUrh1Jm2Efui_ZuAVSbYVePCOBqVepE5Xu4eP10i_0JfUU65JNo9IA0EUbsJkAuuzHLQQ62iQl7tmS6z6MD6c" alt="img" style="zoom:25%;" />

We can also simulate human reads of this length and error rate, then align them back to the human genome and SARS-CoV-2. If errored human material were to align to the SARS-CoV-2 reference, this could result in a false positive. In this simulation, however, we have not been able to generate any such reads (after generating 100,000 reads).

Using this data, we can calculate the false negative and positive rates from these simulated reads. These compare favorably to known rates for qPCR:

|                     | qPCR | 20bp, 5% error |
|---------------------|------|----------------|
| False Negative Rate | 1%   | 0.01%          |
| False Positive Rate | 1.1% | 0%             |


## Sequencing Platforms
In this section, we evaluate the current landscape of sequencing platforms against the technical requirements we have previously established. As we argue in this report, these constraints imply requirements that are substantially more modest than those encountered in research or whole-genome sequencing context. In particular, these are (a) single-base accuracy should be higher than 95%, (b) throughput of at least 10M reads per hour and (c) reads should be at least 18bp. While we would ideally seek to exceed these specifications, building a platform which fits all our requirements requires compromise. In the next section we shall see that current instrumentation has been designed around the requirements of different applications and is a poor fit for point-of-care diagnostics.


### Current Sequencing Landscape
<img width="1000" alt="seqapproaches" src="https://user-images.githubusercontent.com/106965942/226617729-c9743f37-c873-422d-abbd-6f0ea8af98dd.png">


Next-generation sequencing platforms are currently offered by Illumina, MGI, Oxford Nanopore, Pacific Biosciences, SeqLL, GenoMind, Qitan Technology and Thermo (Ion Torrent). A number of other players are also poised to enter the market (Element Biosciences, Singular Genomics, Ultima Genomics). For the most part, however, these players use expired Illlumina intellectual property. Approaches in this category therefore in most cases have similar cost-of-goods-sold (COGS) and performance characteristics as Illumina, and we will not address them here separately.

Despite significant progress in reducing the cost per base in sequencing technology, there are still only around 30,000 sequencers worldwide. This limitation can be attributed to the high absolute costs of instruments and reagents. Most cost reductions have been achieved through multiplexing methods, which involve processing multiple samples simultaneously. However, this approach does not adequately address the prohibitive cost per single run.

The most affordable sequencing option currently available is the Oxford Nanopore Flongle, priced at $90 per run. Despite its low cost, the Flongle is known to have reliability issues, which prevents it from becoming a universally adopted solution. To truly revolutionize the sequencing landscape, it is essential to develop cost-effective, reliable, and accessible sequencing technologies that can be widely implemented.

![img](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F04ac909d-664e-4ba7-8027-eddef4ae3d6c_671x465.png)

Given that existing sequencing approaches have clear limitations, we have two routes forward:

- build on established methodologies to create platforms more fit for purpose
- develop entirely new sensing methodologies and approaches.

A number of other novel sequencing approaches have been proposed. We document these in detail in Appendix B. The most interesting of these for our application are solid-state nanopore approaches, which could potentially retain many of the advantages of protein nanopore platforms, while also potentially rectifying many of its problems. Specifically, solid-state nanopore platforms promise higher accuracy, throughput, lower cost, and simpler sample preparation. However, it is worth noting that this technology is at an experimental stage: research has been underway for more than 20 years and, to date, no reproducible demonstration of near single base resolution sequencing has been shown.

Sequencing technologies are complex and require significant investment. This is most recently apparent in the development of nanopore sequencing: this effort took more than 25 years of active development, and billions of dollars of academic and commercial funding. Given that we are interested in approaches that can make a difference in clinical diagnosis and pandemic preparedness in the next 5-10 years, we discuss lower-risk approaches developing low-cost, high-speed sequencing platforms which build up existing sensing methodologies. It should be noted, however, that while these approaches are lower risk, bringing any novel sequencing platform to commercial launch will ultimately likely require at least \$100M, and that there is still significant market, regulatory and technical risk. Government and philanthropic intervention may therefore be needed, unless a novel way to de-risk development of these technologies is found.

We have reviewed the cost, runtime and sample preparation requirements for a range of platforms, summarized in Table 2.

|                                   | Runtime (10M reads)                                          | Cost (COGS)                                                  | Sample preparation                                           |
| --------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Colony-based approaches           | Illumina cluster generation time alone is at its fastest 60 minutes[⁴⁹](https://www.zotero.org/google-docs/?CvGnN2). This suggests that the minimum overall runtime is unlikely to get below 4 hours | Hundreds of dollars, with an estimated cost floor of ~$50.   | - All approaches use a cyclic chemistry, in which template extension occurs sequentially. This may or may not occur in concert with detection, but it means that a fluidic system is required, adding cost and complexity to the platform.<br />- Library preparation requirements are significant, requiring reverse transcription (in the case of RNA viral diagnostics) and ligation/addition of adapters. |
| Nanopore sequencing               | Runs can be extremely fast (an hour-long run on a Minion could provide nearly 1 million 1Kb reads). This would be sufficient to identify novel viral RNA in a metagenomic sample. | Oxford Nanopore accounts state that goods are sold at 50% margin. This suggests that Minion flow cells would cost \~\$250, and the Flongle flow cell \~\$45. <br />Cost-optimized manufacturing of these devices at scale could lead to COGS <$5 but would require capital investments on the order of $1B. | - Direct RNA readout potentially tractable.<br />- Requires adapters to be added to templates. This process would also need to be integrated into the sample prep instrumentation. |
| Single-molecule optical (PacBio)  | < 1 hour                                                     | Instrumentation and consumables prohibitively costly.        |                                                              |
| Single-molecule optical (Helicos) | <1 hour                                                      | As originally implemented in the 2000s Helicos’ instrumentation cost \>\$100000. However, advances in imaging technologies now allow single=molecule imaging to be performed using \$100 CMOS image sensors. B | - Sequencing unmodified RNA directly on a flow cell has been demonstrated with no need for adapter ligation or other library preparation steps.<br />- Currently requires cyclic chemistry, implying complexity of the reagent and fluidic system. However, this requirement could be avoided with a relatively low-risk R&D effort. |

## Sample Acquisition and Preparation

A complete sample-to-answer metagenomic sequencing platform will require the development of a sample acquisition and preparation system. This will **take samples from patients** and prepare them for introduction to sequencing instrumentation. The first step in a sequencing wor Once a sample has been collected, it needs to undergo a number of preparation steps prior to sequencing. Broadly, we describe these as ***sample preparation*** and ***library preparation***. In a clinically viable platform, sample preparation will be ***integrated into sequencing instrumentation***, such that a clinician need only add the sample to a pre-loaded cartridge and insert it into an instrument, replicating the workflow of sample-to-answer qPCR instrumentation (e.g. the Cepheid GeneXpert).

Both sample and library preparation requirements will vary significantly depending on the *sequencing platform* being used. And both these processes will contribute to the complexity of any integrated infectious disease testing device. In fact, for many approaches the sample and library preparation steps *may be the most costly and time consuming parts of the sequencing process*.

In this section we will discuss sample and library preparation requirements for RNA shotgun metagenomic sequencing of samples.

### Overview of workflows

For the purpose of a ubiquitous sequencing system, sample collection should be **non-invasive** and **economically competitive**. Sample types of interest include 

- nasopharyngeal swabs
- anterior nasal swabs
- breath condensates
- urine
- saliva
- blood

Effective and non-invasive sample acquisition consumables have been developed for use during COVID-19. For ***respiratory conditions***, swab-based anterior nasal collection systems are the natural starting point.

The goal of a **sample preparation** step is to process the sample such that it contains the greatest possible fraction of the material of interest, absent of contaminants. Ideally, samples would require no preparation and raw samples could be loaded directly onto a sequencing instrument. While this could be a long-term aspiration for the field, it seems unlikely that there will be a practically useful approach within the next 5-10 years. Even in the most ambitious scenario, we will likely at least need to dilute the sample in a loading buffer.

More realistically, we will need to remove contaminants and inhibitors, and may wish to remove material that is not of interest (see [Selection](http://sequencing-roadmap.org/sample-prep#selection) below). In this context, the conventional phenol-chloroform based extraction approaches have largely been displaced by silica beads, columns or surfaces.

For platforms only capable of sequencing DNA (Illumina, Ion Torrent), RNA samples will also need to be converted into cDNA prior to library preparation. Fortunately, the isolation and cDNA conversion of RNA samples has been performed at a low cost and scale during COVID-19 and thus should not pose a significant challenge.

*Library preparation* refers to the subsequent preparation steps required to prepare a sample for sequencing. We summarize the current approaches and their complexity below:

| Complexity        | Platform                               | Summary                                                      |
| ----------------- | -------------------------------------- | ------------------------------------------------------------ |
| High Complexity   | Pacific Biosciences, MG                | While current Pacific Biosciences instruments could potentially be capable of direct RNA sequencing no such kits are currently available. The current Pacific Biosciences approach therefore relies on cDNA conversion during sample preparation. These DNA templates are further used to create “Universal SMRTbell templates” for sequencing. This is a complex process which generates circularized DNA as the input to the sequencing process. Similarly MGI requires circularized material for nanoball generation. |
| Medium Complexity | Illumina, Ion Torrent, Oxford Nanopore | Oxford Nanopore, Illumina and Ion Torrent all require adaptor sequences to be added to templates to enable the sequencing process. This is usually performed using either ligation or transposon/topoisomerase based techniques.<br />While Oxford Nanopore have a direct RNA sequencing kit, sample preparation takes \~2 hours. Similarly Illumina and Ion Torrent kits also require \~2 hours of lab time. The fastest sample preparation route here is likely the transposon based approach used as used in Oxford Nanopore’s Rapid DNA sequencing kit, this process takes \~10 minutes. |
| Low Complexity    | Helicos, PacBio (Direct RNA)           | In the case of Helicos direct RNA sequencing[⁴⁶](https://www.zotero.org/google-docs/?rYncGj) where input RNA already has a naturally pre-existing polyA tail in other contexts random hexamer primer single molecule sequencing has been demonstrated[⁵³](https://www.zotero.org/google-docs/?TDYCwr). As such no library preparation steps are required in these cases.<br />Similarly, Pacific Biosciences could adapt their platform for use with single templates (rather than SMRTbell constructs) sacrificing accuracy for simplified library prep, a configuration that was previously supported on older instruments. Failing this, a PolyA tail may be added using readily available polyA tailing kits[⁵⁴](https://www.zotero.org/google-docs/?cpcxLU). This protocol takes \~1 hour. |


While we have discussed sample and library preparation above, there is a third set of processing steps that material often undergoes prior to sequencing. These are often hidden from the user and integrated into the sequencing process itself. However, if we are to build a complete integrated solution they must be considered.

Most significantly these “pre-sequencing” steps include the **localized amplification** of a single template. These include:

- Clusters (Illumina - Bridge Amplification)
- DNA amplified beads (Ion Torrent, Genapsys, Ultima Genomics)
- DNB (DNA Nanoballs - MGI).

DNA amplified beads in particular often require dedicated instrumentation (for example the Ion Torrent OneTouch), adding significant complexity to a complete sequencing solution.

### Selection

We may want to remove unwanted material prior to sequencing. This is material that would otherwise appear as background sequence reads, or otherwise interfere with the sequencing process. In other cases background human genomic material may contribute personally identifiable information (PII) and for regulatory reasons may require removal prior to sequencing.

Removal of unwanted material also allows us to reduce the number of reads we need to generate to reach equivalent sensitivity (see “Sensitivity”).

Typically at least the nucleic acid of interest will be selected for. This will involve the use of a DNase or RNase to digest either DNA or RNA. Which could otherwise form part of the sequencing library.

In RNA sequencing experiments ribosomal RNA (rRNA) is a significant contaminant. Kits are available[⁵⁵](https://www.zotero.org/google-docs/?dWnu4m) which will target and degrade rRNA, or other genomic RNA contaminants. However these approaches add complexity, for example the kit linked here requires nearly 2 hours of lab time (8mins hands on).

Beyond this other selection methods may be of interest. Most typically size selection and selection of material contained within viral envelopes. Unfortunately, as noted in Understanding the Target, the majority of viral material may be degraded in our samples, suggesting that it exists outside of the viral envelope. This material also appears to be similar in fragment size to background human derived RNA. As such particle, and RNA size selection methods may be of limited utility.

### Integrated Approaches

This section has discussed *existing* library preparation approaches. It’s important to note that current platforms have been designed to be *versatile* and serve a number of applications using the same reagent kits and flowcells. 

However, we can further **simplify the library preparation process if we sacrifice this versatility**. For example, as discussed above, for Helicos direct RNA sequencing where naturally pre-existing polyA tails are present, no additional sample preparation is required. This is because the Helicos/SeqLL flow cells are coated with poly(dT) oligonucleotides to capture these polyA-tailed templates.

We can imagine an approach where flow cells are coated with different oligonucleotides, enabling other templates to be captured. For example, the surface could be coated with random hexamer oligonucleotides allowing a material to be directly captured on the flowcell. This would allow material to be captured on the flow cell without additional library preparation steps. A targeted approach could also be employed where oligonucleotides target specific known sequences (for example known viral sequence).

To build an effective sample-to-answer platform we will need to automate the steps described above in a low cost platform. Such an automation system is currently unavailable for use on a single sample basis. This is largely because there is no current market for a fixed protocol metagenomic sample preparation system. However as we shall see, viable approaches have already been demonstrated for use in qPCR sample-to-answer systems. We therefore view the development of automated sample preparations systems as a low technical risk problem.

A number of integrated sample and library preparation devices are available or under development. Existing commercial approaches are largely built around pipette robots, and a number of turnkey platforms are available for use with Illumina sequencers[⁵⁶](https://www.zotero.org/google-docs/?tgNg6l). These almost exclusively are designed to process \>8 samples, to support larger labs, require skilled personnel, and are not suitable for use in a point of care context.

Digital fluidic platforms (Voltrax[⁵⁷](https://www.zotero.org/google-docs/?1gEuyQ), Volta[⁵⁸](https://www.zotero.org/google-docs/?fx2Y8I), Illumina Neoprep[⁵⁹](https://www.zotero.org/google-docs/?sInpeV)) are also available. To date these have largely been used in a research context. These instruments can automate complex workflows in a small footprint. However, they are generally designed to address research requirements at relatively high cost, and are not integrated into the sequencing platform itself.

One company (DNAe) is currently developing a sample-to-answer sequencing platform[⁶⁰](https://www.zotero.org/google-docs/?ZK4aFk). However, from available information, it is unlikely that this platform will be applicable for hypothesis-free infectious disease testing.

The deployment of a viral MGS-based diagnostic platform would require a new generation of automated sample and library preparation instrumentation. In designing these, it is possible to take a page out of fully-integrated qPCR sample-to-answer platforms[⁶¹](https://www.zotero.org/google-docs/?tsg7sb) are available. Notable examples are the Cepheid GeneXpert, GenMark ePlex and Abbott ID NOW. More recently, sample-to-answer platforms specifically targeting SARS-CoV-2 have also been developed (e.g. DNANudge developed by TTP).

These tools integrate both sample preparation and molecular diagnostics platforms into single instruments and consumables. Three approaches stand out in this context:

1. those which use traditional cartridge integrated fluidic systems (Cepheid, DNANudge), 
2. novel fluidic approaches (Digital fluidics, GenMark), and 
3. approaches which seek to simplify the chemistry, removing the fluidic system entirely (Abbott ID NOW).

**Digital fluidic platforms** tend to be more expensive, with the Genmark test sold at \$157[⁶²](https://www.zotero.org/google-docs/?Zs1EnC), and aimed at a larger number of targets.

**Traditional fluidic approaches** (Cepheid Genexpert, DNANudge) have an estimated manufacturing cost of \$3[⁶³](https://www.zotero.org/google-docs/?nqu5ni), and are typically sold for \~\$20. These platforms incorporate the necessary reagents to lyse and extract RNA from a sample. As noted above, for some single-molecule platforms (Helicos-like single molecule direct RNA sequencing), this provides sufficient sample preparation to proceed to sequencing.

In the DNANudge post-clean up phase, cDNA is eluted into an imaging region. This could be replaced with a single-molecule imaging region using a non-cyclic chemistry. Alternatively, additional reagents could be added to enable adapter ligation or transposon=based adapter addition. In this case the imaging window could be replaced with a nanopore array.

Both these approaches could be implemented without unduly increasing the complexity beyond that of the DNANudge device (manufactured and developed by TTP). We can therefore expect such an integrated sample prep and sequencing instrument to have a **COGS comparable to the DNANudge and other sample-to-answer platforms such as the Genexpert (~$3)**.

Beyond this, it is possible that **surface amplification** (Illumina - bridge amplification) and **cyclic sequencing** could be integrated into the sequencing cartridge (as in the iSeq). However, as discussed in our chapter on , this may result in a platform that no longer meets our time-to-answer a cost requirements.
