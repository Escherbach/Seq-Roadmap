# Background

## **Summary**

In this section, we discuss the COVID-19 pandemic and build a framework for thinking about pandemics and pandemic response. There are several conclusions we can draw from this. Firstly, we can think of pandemics occurring in three phases:

Phase 1: Unknown and unmonitored  
Phase 2: Known, but unmonitored.  
Phase 3: Pandemic response capability developed and deployed.

Secondly, while sequencing based diagnostics offer significant advantages over traditional approaches (e.g. qPCR), they have not gained traction during COVID-19 beyond use for tracking variants that give rise to new strains. There are two strong factors which have prevented adoption:

- Cost: qPCR costs \~\$1 where sequencing costs \$50 to \$100 per sample/run.

- Market: the value of sequencing over qPCR is not well understood.

Applying metagenomic sequencing in a pandemic preparedness program will face similar issues. The value to both the user and clinicians of metagenomic sequencing-based diagnostics needs to be made clear. The cost of such a diagnostic test needs to be low enough to allow it to be economically performed.

Our most likely route here is to provide a universal metagenomic sequencing-based diagnostic for respiratory (and other) conditions. In one such scenario, a symptomatic individual would visit a primary care physician to be evaluated. The physician could perform a metagenomic sequencing-based test to detect both known and unknown pathogens, which would provide a valuable diagnostic to guide care. For example, an anterior nasal swab test could determine if a patient had a viral, bacterial or fungal infection, determine the strain of pathogen, and ideally identify any anti-microbial resistance genes to guide treatment. Essentially this provides an enhanced full respiratory diagnostic panel for the cost of a Flu/RSV/COVID qPCR kit.

This is a clear value to both patients and clinicians and builds a more robust culture to detect and contain new viruses. And only by displacing qPCR as the first line diagnostic tool of choice, can we provide the robust pandemic preparedness technology we desire.

When unknown RNA or DNA is detected the information would be sent to a central (likely cloud-based) monitoring center. Providing a pandemic early warning system.

The most significant risk here is market and regulatory. But reports suggest there is demand from patients and clinicians.

The following sections will discuss the requirements of such a system.

## **Early detection and mass testing**

COVID-19 was the first worldwide pandemic to occur in modern times. And while we can draw some lessons from previous novel viral outbreaks (SARS, MERS, Ebola), we must principally look to COVID-19 when evaluating modern methods for pandemic response.

We can think of the global response to COVID-19 as occurring in 3 distinct phases.

Phase 1: Unknown and unmonitored  
Phase 2: Known, but unmonitored.  
Phase 3: Pandemic response capability developed and deployed.

![Group](media/image5.png)

### Phase 1: Unknown and unmonitored - COVID-19 

In COVID-19 and prior viral outbreaks, it became clear that our methods for detecting a new viral outbreak are not up to the task. While the index case of SARS-CoV-2 has yet to be identified, it is clear that more than a month passed between the beginning of human-to-human transmission and its identification as the causative agent of respiratory disease cases in the Wuhan region[¹](https://www.zotero.org/google-docs/?OCagce).

Disease response centers monitor spikes in patients with novel symptoms, this monitoring relies largely on self-reporting by on the “astute physician” to notice unusual signs of an illness (a challenging task given the similarity of symptoms across a wide range of pathogens) and on self-reporting by hospitals, with guidelines varying in countries across the world[¹](https://www.zotero.org/google-docs/?EzO1X2). Therefore, we are likely to only notice an outbreak when a critical mass of infections has taken place. At this point of the exponential growth typically exhibited by pandemic-capable pathogens, an outbreak is substantially more difficult to contain than it is at earlier phases.

Once a suspected novel virus has been identified, it may be isolated and sequenced. In the case of SARS-CoV-2, known viruses were first ruled out through antigen kits, then confirmed by qPCR, prior to metagenomic sequencing which identified a novel viral strain.[²](https://www.zotero.org/google-docs/?AQxYU8)

The availability of the viral genome is a critical milestone in pandemic response. Not only does it provide the foundation for the *development of diagnostic kits* (qPCR and other), but it also allows the first steps toward *vaccine development* to begin.

Our goal is to move from this slow, pathogen-targeted status quo to a more rapid, pathogen- agnostic approach to outbreak detection and response. Two potentially complementary approaches have been proposed: *environmental monitoring* and *individual monitoring*.

#### Environmental monitoring 

In an environmental monitoring approach, data is collected on pathogen genomic material shed into the environment. Example samples include wastewater or air filters at key locations. Pathogen-targeted environmental monitoring approaches have successfully been used during the COVID-19 pandemic to monitor variants circulating within a population[³](https://www.zotero.org/google-docs/?WbaZB1).

Metagenomics-based environmental monitoring approaches have the potential to perform pathogen-agnostic monitoring at the population level[⁴](https://www.zotero.org/google-docs/?ivdYrO), but face distinct challenges in system sensitivity and cost. Additionally, they lack a commercial engine to drive their ubiquitous adoption.

However, metagenomics-based environmental monitoring may eventually be worth the cost in a layered biodefense system (i.e. for detecting pathogens with a longer latency or subtle initial symptoms), especially if progress in high-throughput sequencing, sample preparation (e.g. depletion of known genomic material), and computational analysis is achieved in the coming years. These challenges are worthy of a separate roadmapping exercise. However, in this roadmap, we focus on an approach where we see a clearer path to pathogen-agnostic early outbreak detection within the coming 5-10 years, namely individual monitoring.

#### Individual monitoring 

In an individual monitoring approach, samples would be isolated from individuals for testing. This could be done either at the point of care or in a sentinel context. Below, we focus on the former.

In samples acquired from patients infected by SARS-CoV-2, the total RNA from nasopharyngeal samples contains viral RNA at up to 5% when ribosomal RNA (rRNA) is depleted.[⁵](https://www.zotero.org/google-docs/?OU3DwX) At this level of abundance, direct sequencing of total RNA would almost certainly reveal the presence of a novel, SARS-CoV-2-like respiratory virus.[^1]

In addition to this abundance of signals for pathogen detection, individuals showing symptoms (fever and or flu-like symptoms) may already be inclined to seek medical assistance. Reports suggest that patients increasingly want to receive a diagnosis rather than “non-specific upper respiratory infection”, the majority diagnosis in ambulatory care visits for respiratory issues.

For instance, Emily Volk[⁶](https://www.zotero.org/google-docs/?qDxcPN) reports:

> *“Frankly, patient experience scores increase when patients leave our care and have a name for the thing that is bothering them even if there isn’t a targeted antibiotic or antimicrobial that has been identified, that would work against the pathogen. It still is comforting to patients and their families to have a name for the illness that they have.”*

Clinicians themselves are becoming more inclined to order broader panels. According to Emmanuel André[⁶](https://www.zotero.org/google-docs/?DXh03H):

> *“The single pathogenic approach will progressively disappear. Why? Because it’s simply not efficient from a clinical perspective, from a lab perspective and care requires a more comprehensive approach. Where I think we’re going is toward broader panels.”*

Metagenomic sequencing provides the broadest of all possible panels. As such, a metagenomic sequencing-based approach, if it can be as cheap as qPCR testing, may quickly gain widespread adoption even in the absence of planned pandemic prevention efforts.

Any unknown pathogen sequence identified by these tests may be transmitted to pandemic monitoring centers, allowing novel human pathogen cases to be identified almost as soon as they occur.

### Phases 2 & 3: Known but unmonitored plus test development 

The SARS-CoV-2 genome was made publicly available in January 2020, more than two months after the first human transmission. For current diagnostic approaches, this is a significant issue. Each new virus requires a new test to be developed, approved, and deployed. When potentially hundreds of millions of tests are required, this is a huge logistical issue.

In the case of COVID-19, it took more than 4 months for 1 million tests to be performed in the US and 9 months to deploy 100 million tests[⁷](https://www.zotero.org/google-docs/?s9uX3H). Logistical and regulatory issues, therefore, limit our ability to engage in “track and trace” operations allowing the pandemic to proceed largely unmonitored.

In order to remove the long ramp-up associated with kit deployment, we either need kits that can be more rapidly produced or that are pathogen-agnostic. The ability to stockpile tests without the need to predict the pathogen they will be used for is a distinct advantage.

New approaches to DNA synthesis (enzymatic approaches) could potentially help ramp up and distribute the production of qPCR kits once a novel threat has been identified.

However, a more practical and versatile proposition is to design our diagnostic approach using the same techniques used to identify new viral outbreaks currently: metagenomic sequencing.

In this approach, our diagnostic instruments are *already* deployed as part of our pandemic monitoring program and provide patients with valuable diagnostic information regarding their suspected infections, ideally building a culture where the majority of suspected respiratory infections receive a full metagenomic-based diagnostic test.

## Technical requirements and Bottlenecks in current approaches 



Our proposed future solution to pandemic monitoring is, therefore, to use metagenomic sequencing to address all phases of the pandemic. We will consider how such a system might be built using existing platforms, what the cost barriers to adoption are, and how we might address the deficiencies of these platforms.

It is of note that a number of sequencing-based diagnostic approaches have been attempted during COVID-19. However, they have largely failed to gain traction and cumulatively represented \<1% of the testing used to detect and monitor COVID-19 infections[⁸](https://www.zotero.org/google-docs/?mhRwMO):

There are a number of reasons for this which we summarize in the table below:

|                      | qPCR            | Metagenomic Sequencing |
|----------------------|-----------------|------------------------|
| Cost-of-goods (COGs) | \$1 to \$5      | \$15 to \$100          |
| Automation           | Widely deployed | Limited                |
| Time to answer       | \< 1 hour       | Days to Weeks          |

Unless these issues are addressed, metagenomic sequencing-based approaches are unlikely to gain widespread adoption.

### Cost

Illumina’s (current market leader in sequencing) cheapest runs cost \~\$300 to \$500[⁹](https://www.zotero.org/google-docs/?NJMTcC). As such, healthcare providers are unlikely to use these instruments for sequencing single samples. Batching and multiplexing multiple samples onto a single sequencing run can significantly reduce the cost per sample, but introduces a delay before sequencing can begin. The delay is dependent on the nature of the testing facility and the number of samples being received per day, but typically, this is on the order of a week.

Other instruments (for example, Oxford Nanopore’s Flongle) cost \~\$100[¹⁰](https://www.zotero.org/google-docs/?QpfDWf), which could enable fewer samples to be multiplexed, perhaps on a daily basis.

However, a delay of days to weeks is likely unacceptable in an infectious disease diagnostic context where we ideally want to provide results as rapidly as possible.

Furthermore, and perhaps most problematically, multiplexing multiple samples onto a single chip significantly reduces the sensitivity of the test since the sequence coverage per sample reduces proportional to the number of samples.

Therefore the high single-run cost for current instruments makes them a poor fit for diagnostic applications. This is the case even if we look at the COGS (Illumina \$50 to \$100s, Oxford Nanopore \$50 to \$450 based on stated margins^([1](https://www.zotero.org/google-docs/?uZfJ69) [12](https://www.zotero.org/google-docs/?tljpmF)). Cheaper options could make running single-sample tests economically viable.

### Automation

Sequencing-based assays are complex and typically require multiple hours of skilled labor to execute (both in the wet lab and data analysis).

A pushbutton “sample-to-answer” sequencing platform could allow minimally-trained personnel to load a sample and walk away from the device. Such a platform could have a major impact on the ease of implementation of sequencing-based diagnostics. Yet, no sample-to-answer sequencing platform currently exists.

Efforts have been made to automate parts of the sample preparation and library preparation process workflows, but these have largely addressed research applications or users who are comfortable investing effort in developing automation systems to process large numbers of samples in centralized labs. No low-cost fixed protocol suitable for use in a clinical context is available.

### Time to Answer

We previously discussed how the requirement of multiplexing can increase diagnostic turnaround time by days to weeks. Sending samples to a centralized lab followed by the execution of complex workflows by trained personnel also adds significantly to the time to answer. Indeed, current metagenomic-based pathogen tests often have a 2-4 week turnaround time[¹³](https://www.zotero.org/google-docs/?7jVZxG).

On the sequencing technology front, Illumina’s fastest sequencing runs are \~4 hours[¹⁴](https://www.zotero.org/google-docs/?RCkl9s), though their runs typically fall between 24-48 hours. In combination with the factors discussed above, we believe this is too slow to provide valuable clinical feedback to patients in many cases. However, nanopore and single-molecule approaches can currently provide sequencing data in a \<1-hour timeframe.

[Sample and library preparation](https://sequencing-roadmap.org/sample-prep) are also significant bottlenecks here. This is strongly dependent on the sequencing technology being used. Standard protocols typically take \>2 hours. In later sections, we discuss approaches which can provide sequencing-ready DNA in \~10 minutes[¹⁵](https://www.zotero.org/google-docs/?gUoxVG).

[^1]: We justify this in “[Sensitivity](https://sequencing-roadmap.org/sensitivity)”
