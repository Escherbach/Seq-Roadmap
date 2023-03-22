# Sequencing Platforms: Evolution and State of the Art
In this section, we evaluate the current landscape of sequencing platforms against the technical requirements we have previously established:

1. Platforms should process single samples.
2. Time to answer should be less than 1 hour.
3. The COGS should be comparable to qPCR (<$10).
4. Sensitivity should be comparable to qPCR.

As we argue in this report, these constraints imply requirements that are substantially more modest than those encountered in research or whole-genome sequencing context. In particular, these are (a) single-base accuracy should be higher than 95%, (b) throughput of at least 10M reads per hour and (c) reads should be at least 18bp.

While we would ideally seek to exceed these specifications, building a platform which fits all our requirements requires compromise. In the next section we shall see that current instrumentation has been designed around the requirements of different applications and is a poor fit for point-of-care diagnostics.

* TOC
{:toc}

### Sequencing Landscape
<img width="1000" alt="seqapproaches" src="https://user-images.githubusercontent.com/106965942/226617729-c9743f37-c873-422d-abbd-6f0ea8af98dd.png">


Next-generation sequencing platforms are currently offered by Illumina, MGI, Oxford Nanopore, Pacific Biosciences, SeqLL, GenoMind, Qitan Technology and Thermo (Ion Torrent).

A number of other players are also poised to enter the market (Element Biosciences, Singular Genomics, Ultima Genomics). For the most part however, these players use expired Illlumina intellectual property. They therefore in most cases have similar cost-of-goods-sold (COGS) and performance characteristics, and we will not address them here. They are however discussed in detail in Appendix B.

The relevant specifications of existing commercial platforms are summarized below:

[TABLE]

As discussed in Understanding the Target, we can expect to have \~6ng/mL of total RNA. The majority of the above sequencing platforms can not directly sequence this sample type. Either they are unable to sequence RNA directly (Illumina, MGI, PacBio, Ion Torrent) or sample input requirements are too high (ONT).

Surprisingly the only platform capable of directly sequencing such samples is provided by SeqLL, likely the smallest player in the next-gen sequencing market. This company provides a platform previously developed by defunct sequencing startup Helicos.

In terms of run time, only Oxford Nanopore and Pacific Biosciences platforms provide results within an hour (required to provide results within an ambulatory care visit, and comparable to current qPCR platforms).

### Evolution of Existing Approaches

Given that existing sequencing approaches have clear limitations, we have two routes forward. Either we can build on established methodologies to create platforms more fit for purpose, or we can develop entirely new sensing methodologies and approaches.

Sequencing technologies are complex and require significant investment; this is most recently apparent in the development of Nanopore sequencing. This effort took more than 25 years of active development, and billions of dollars of academic and commercial funding.

In this section we discuss lower risk approaches developing low cost, high speed sequencing platforms which build up existing sensing methodologies. It should be noted however, that while these approaches are lower risk, bringing any novel sequencing platform to commercial launch will likely require at least \$100M, and that there is still significant market, regulatory and technical risk.

#### Colony-based approaches

Current market leading approaches use amplified copies of a single template on a surface or bead. The most popular of these is provided by Illumina, using bridge amplification.

Illumina cluster generation time is at its fastest 60 minutes[⁴⁹](https://www.zotero.org/google-docs/?CvGnN2). This limitation alone suggests that colony based approaches will require significant development to meet our run time requirements (\<1 hour).

Beyond colony generation, all current colony based approaches use a cyclic chemistry. In this approach template extension occurs sequentially. This may or may not occur in concert with detection, but it means that a fluidic system is required. This adds cost and complexity to the platform, and while we believe Illumina instruments may be able to achieve a COGS near \$50 per run, \$5 or less seems like a challenging goal for a complex fluidic system and therefore reagent cartridge.

One route to removing the complexity of a cyclic chemistry could be through the use of photo-cleavable terminators, such as the Lightning terminators developed by LaserGen[⁵⁰](https://www.zotero.org/google-docs/?kh7rF1). Using this approach, rather than using a cleavage reagent, terminators would be unblocked with a UV light source. This would dramatically simplify the platform and could help significantly reduce consumable costs.

Overall, we believe that there are significant challenges to using colony based approaches when developing low cost diagnostics consumables.

Beyond the issues stated above, the library preparation requirements are significant, requiring reverse transcription (in the case of RNA viral diagnostics) and ligation/addition of adapters. Automating and integrating these sample prep stages itself brings costs which we would rather avoid.

#### Nanopore

Oxford Nanopore and Qitan Technology have been extremely successful in bringing to market the first single molecule direct electrical detection sequencing platforms. As noted above Nanopore platforms have several desirable characteristics. Firstly, runs can be extremely short (an hour long run on a Minion could provide nearly 1 million 1Kb reads). This would be sufficient to identify novel viral RNA in a metagenomic sample. The platform can also potentially provide a direct readout from RNA. Enabling such experiments would require significant developments in sample preparation, but seems tractable.

However, a current key limitation for Nanopore sequencing is the COGS of the sequencing consumable. At present Oxford Nanopore accounts state that goods are sold at 50% margin. This suggests that Minion flow cells would cost \~\$250, and the Flongle flow cell \~\$45. As described elsewhere, for broad adoption we feel that we need a COGS nearer to the \$5 range including all sample preparation reagents.

For a Nanopore based diagnostic platform we would therefore need to reduce the COGS by one to two orders of magnitude. This may be possible, but is extremely challenging. A reduction in feature size (from wells of \~150um currently) would help with this. Integration of the current amplification analog frontend onto the sensing substrate, or out of the consumable could also help reduce COGS.

Like Illumina sequencing, Oxford Nanopore sequencing also requires adapters to be added to templates. This process would also need to be integrated into the sample prep instrumentation.

Overall, the most significant risks here are the relatively high cost of goods, and the lack of a clear path to low cost consumables.

#### Single Molecule Optical

Two single molecule optical approaches have been successfully brought to market: Helicos (SeqLL) and Pacific Biosciences.

The Pacific Biosciences approach uses zero mode waveguides in its current embodiment; these are integrated into a CMOS sensing platform. While the platform can potentially provide a sequencing output within an hour the instrumentation and consumables are costly. Therefore many of the cost-of-goods issues with Nanopore sequencing likely also exist here. The platform however could potentially be adapted to sequence RNA directly.

An evolution of the Helicos approach seems more practical here, and we would suggest it is the most practical route based on known sensing methodologies. While as originally implemented in the 2000s Helios’ instrumentation cost \>\$100000, advances in imaging technologies now allow single molecule imaging to be performed using \$100 CMOS image sensors. The basic approach also requires minimal sample preparation. Sequencing unmodified RNA directly on a flow cell has been demonstrated with no need for adapter ligation or other library preparation steps.

The Helicos approach has two key limitations for application in diagnostic instrumentation. Firstly, Helicos data quality is significantly worse than any other current player in next generation sequencing. The platform generated short reads (\<50bp) and had a relatively high error rate (\~3% overall). This was a significant issue when addressing whole genome sequencing. However, for use in diagnostics and with short viral genomes, relatively high error rates can be tolerated. Additional strategies may also be developed to reduce error rates and increase read lengths.

The second issue is that the Helicos approach retains the complexity of a cyclic chemistry associated with the colony based approaches described above.

There are however a number of strategies that would remove the requirement for a cyclic chemistry in a single molecule optical sequencing platform. One of these is the use of stochastic label removal as proposed by Reticula (disclosure, the founder of Reticula was involved in the development of this report). This, and related approaches would dramatically reduce the complexity of the reagent and fluidic system.

This approach has well characterized technical risks (as the single molecule optical detection method has already been demonstrated by Helicos) and free-running detection of labels has recently been shown to work well in DNA-PAINT and related approaches. It also requires a very simple integrated sample preparation system nearly identical to that used in qPCR.

### Blue-sky Technologies

A number of other novel sequencing approaches have been proposed, these are documented in detail in Appendix B.

The most interesting of these for our application are solid state nanopore approaches. Solid state Nanopore approaches promise many of the advantages of Oxford Nanopore’s protein nanopore platform but also offer the possibility of rectifying many of the problems. Specifically, solid state nanopore platforms promise to be higher accuracy, higher throughput, lower cost, and require simpler sample prep.

However solid state nanopore research has been underway for more than 20 years and to date no reproducible demonstration of near single base resolution sequencing has been shown.

Oxford Nanopore’s protein nanopore sequencing platform uses ionic current blockages to detect nucleotides as they translocate through a biological nanopore. The Oxford Nanopore platform uses biological pores with single digit nanometer scale features (1.2 nm constriction in a 2nm barrel). The reliable fabrication of solid state nanopores with equivalent feature size would be extremely challenging.

If fabrication challenges were solved, it seems likely that Oxford Nanopore’s enzymatic motion control strategy could be combined with a solid state sensing platform. Such a platform may unfortunately not have any compelling advantage over a protein nanopore sequencing platform. Namely, the sequencing speed will likely be the same (420bp/s), and potentially accuracy limitations associated with the limited ability to accurately control translocation of the strand through the pore. It could however be more easily washable in situ, allowing the sensing mechanism to be reused indefinitely for multiple samples.

The readout read of an ionic current detection nanopore is likely limited to \< 1000bp/s, based solely on the number of and mobility of charge carriers. Other approaches have been suggested that address nanopore sequencing accuracy and speed limitations.

One example of this is tunneling current sensing. Here transverse electrodes are used to register a tunneling current. As nucleotides translocate through the sensing region they interfere with this tunneling current. This signal is then used to determine the sequence of the template.

This approach has been pursued commercially (Quantum Biosystems, Genvida) and in a number of academic labs. While a number of groups have shown that DNA can be imaged using tunneling currents (STM) there have been no reproducible results showing sequencing data on strand. Tunneling current detection promises higher accuracy (as larger currents can be generated), and higher readout speeds. But remains at present a research activity which may take decades to fulfill its promise, that is if insurmountable physical limitations are not discovered.

Nanopore embedded field effect sensors have also been proposed. These would embed a FET inside a nanopore, where the dielectric changes produced by nucleosides as they pass in close contact to the sensor would be detected through changes in the electric field. This approach is being pursued by startup iNanoBio. iNanoBio was founded 14 years ago, and to date no sequencing results have been reported. iNanoBio suggests that they may be able to reach extremely high readout speeds (millions of bases/s). However, related techniques such as scanning capacitance microscopy (SCM) have so far been limited to a few kilohertz[⁵¹](https://www.zotero.org/google-docs/?OyaVmX), suggesting this might be challenging.

Various other novel nanopore platforms are also in development such as optical nanopore platforms (Quantapore) or SBS-Nanopore systems (Genia, AxBio). In many cases the advantages of these platforms, particularly for diagnostic applications, is unclear.
