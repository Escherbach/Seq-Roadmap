# Sample Acquisition and Preparation

> **Summary:** The deployment of a viral MGS-based diagnostic platform will require a new generation of automated sample and library preparation instruments that are simple to use, economically competitive and that remove issues with contamination. Instrumentation from qPCR systems can be adapted with minimal technical risk.


<img src="https://lh5.googleusercontent.com/pjMPTRucxhSo8rMBSOmjHcpy-RNWHAAaOSLOvvAdyzECOurvjLs2IEhrjaemkVwpKM5pWe1Shk6_r6KsleX-LACNjCMTNV33dV4t137NGPeHZeIBvQlLNsU9BZPVfwb97eXdGgA_pNPx7qMfrmscNu0" alt="img" style="zoom: 25%;" /><img src="https://lh5.googleusercontent.com/SBEwKqvHI3q-1lpkT8fntKoQTnuk_awWFY87iL_ZK8WhYdaT41XXI_TPKWiYJLulw1MTBzEuot9upRh98bpgBRZ-kp_gbKj661YOEEkoqgMZXGKSK4Up26weixzeWBkG8zKONo-YlA1Nex6TIoT3Euo" alt="img" style="zoom: 25%;" />

*DNANudge and Cepheid sample-to-answer cartridges. Cepheid ship ~36 million units a year.*

* TOC
{:toc}

## Overview of Current Workflows

A complete sample-to-answer metagenomic sequencing platform will require the development of a sample acquisition and preparation system. This will **take samples from patients** and prepare them for introduction to sequencing instrumentation. The first step in a sequencing wor Once a sample has been collected, it needs to undergo a number of preparation steps prior to sequencing. Broadly, we describe these as ***sample preparation*** and ***library preparation***. In a clinically viable platform, sample preparation will be ***integrated into sequencing instrumentation***, such that a clinician need only add the sample to a pre-loaded cartridge and insert it into an instrument, replicating the workflow of sample-to-answer qPCR instrumentation (e.g. the Cepheid GeneXpert).

Both sample and library preparation requirements will vary significantly depending on the *sequencing platform* being used. And both these processes will contribute to the complexity of any integrated infectious disease testing device. In fact, for many approaches the sample and library preparation steps *may be the most costly and time consuming parts of the sequencing process*.

In this section we will discuss sample and library preparation requirements for RNA shotgun metagenomic sequencing of samples.

### Sample Acquisition

For the purpose of a ubiquitous sequencing system, sample collection should be **non-invasive** and **economically competitive**. Sample types of interest include 

- nasopharyngeal swabs
- anterior nasal swabs
- breath condensates
- urine
- saliva
- blood

Effective and non-invasive sample acquisition consumables have been developed for use during COVID-19. For ***respiratory conditions***, swab-based anterior nasal collection systems are the natural starting point.

### Sample Preparation

The goal of a sample preparation step is to process the sample such that it contains the greatest possible fraction of the material of interest, absent of contaminants.

Ideally, samples would require no preparation and raw samples could be loaded directly onto a sequencing instrument. While this could be a long-term aspiration for the field, it seems unlikely that there will be a practically useful approach within the next 5-10 years. Even in the most ambitious scenario, we will likely at least need to dilute the sample in a loading buffer.

More realistically, we will need to remove contaminants and inhibitors, and may wish to remove material that is not of interest (see [Selection](http://sequencing-roadmap.org/sample-prep#selection) below). In this context, the conventional phenol-chloroform based extraction approaches have largely been displaced by silica beads, columns or surfaces.

For platforms only capable of sequencing DNA (Illumina, Ion Torrent), RNA samples will also need to be converted into cDNA prior to library preparation. Fortunately, the isolation and cDNA conversion of RNA samples has been performed at a low cost and scale during COVID-19 and thus should not pose a significant challenge.

### Library Preparation

*Library preparation* refers to the subsequent preparation steps required to prepare a sample for sequencing. We summarize the current approaches and their complexity below:

| Complexity        | Platform                               | Summary                                                      |
| ----------------- | -------------------------------------- | ------------------------------------------------------------ |
| High Complexity   | Pacific Biosciences, MG                | While current Pacific Biosciences instruments could potentially be capable of direct RNA sequencing no such kits are currently available. The current Pacific Biosciences approach therefore relies on cDNA conversion during sample preparation. These DNA templates are further used to create “Universal SMRTbell templates” for sequencing. This is a complex process which generates circularized DNA as the input to the sequencing process. Similarly MGI requires circularized material for nanoball generation. |
| Medium Complexity | Illumina, Ion Torrent, Oxford Nanopore | Oxford Nanopore, Illumina and Ion Torrent all require adaptor sequences to be added to templates to enable the sequencing process. This is usually performed using either ligation or transposon/topoisomerase based techniques.<br />While Oxford Nanopore have a direct RNA sequencing kit, sample preparation takes \~2 hours. Similarly Illumina and Ion Torrent kits also require \~2 hours of lab time. The fastest sample preparation route here is likely the transposon based approach used as used in Oxford Nanopore’s Rapid DNA sequencing kit, this process takes \~10 minutes. |
| Low Complexity    | Helicos, PacBio (Direct RNA)           | In the case of Helicos direct RNA sequencing[⁴⁶](https://www.zotero.org/google-docs/?rYncGj) where input RNA already has a naturally pre-existing polyA tail in other contexts random hexamer primer single molecule sequencing has been demonstrated[⁵³](https://www.zotero.org/google-docs/?TDYCwr). As such no library preparation steps are required in these cases.<br />Similarly, Pacific Biosciences could adapt their platform for use with single templates (rather than SMRTbell constructs) sacrificing accuracy for simplified library prep, a configuration that was previously supported on older instruments. Failing this, a PolyA tail may be added using readily available polyA tailing kits[⁵⁴](https://www.zotero.org/google-docs/?cpcxLU). This protocol takes \~1 hour. |

### Pre-sequencing Steps (Cluster and Colony Generation)

While we haveve discussed sample and library preparation above, there is a third set of processing steps that material often undergoes prior to sequencing. These are often hidden from the user and integrated into the sequencing process itself. However, if we are to build a complete integrated solution they must be considered.

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

## Automated and Integrated Solutions

To build an effective sample-to-answer platform we will need to automate the steps described above in a low cost platform. Such an automation system is currently unavailable for use on a single sample basis. This is largely because there is no current market for a fixed protocol metagenomic sample preparation system. However as we shall see, viable approaches have already been demonstrated for use in qPCR sample-to-answer systems. We therefore view the development of automated sample preparations systems as a low technical risk problem.

### Current Solutions

A number of integrated sample and library preparation devices are available or under development. Existing commercial approaches are largely built around pipette robots, and a number of turnkey platforms are available for use with Illumina sequencers[⁵⁶](https://www.zotero.org/google-docs/?tgNg6l). These almost exclusively are designed to process \>8 samples, to support larger labs, require skilled personnel, and are not suitable for use in a point of care context.

Digital fluidic platforms (Voltrax[⁵⁷](https://www.zotero.org/google-docs/?1gEuyQ), Volta[⁵⁸](https://www.zotero.org/google-docs/?fx2Y8I), Illumina Neoprep[⁵⁹](https://www.zotero.org/google-docs/?sInpeV)) are also available, to date these have largely been used in a research context. Potentially these instruments can automate complex workflows in a small footprint. But they are generally designed to address research requirements at relatively high cost, and are not integrated into the sequencing platform itself.

One company (DNAe) is currently developing a sample-to-answer sequencing platform[⁶⁰](https://www.zotero.org/google-docs/?ZK4aFk). However, it is unclear if this platform will be applicable for hypothesis-free infectious disease testing.

### New Solutions

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
