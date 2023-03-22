# Metagenomic Sequencing and Early Pandemic Detection

COVID-19 was the first worldwide pandemic to occur since the early 20th century. And while we can draw some lessons from previous novel viral outbreaks (SARS, MERS, Ebola), we must principally look COVID-19 offers the most relevant insights when evaluating modern methods for pandemic response.

In COVID-19 and prior viral outbreaks, it became clear that our methods for detecting a new viral outbreak are not up to the task. While the index case of SARS-CoV-2 has yet to be identified, it is clear that more than a month passed between the beginning of human-to-human transmission and its identification as the causative agent of respiratory disease cases in the Wuhan region[¹](https://www.zotero.org/google-docs/?OCagce).

In this section, we discuss the COVID-19 pandemic and build a framework for thinking about pandemics and pandemic response. There are several conclusions we can draw from this. Firstly, we can think of pandemics occurring in three phases:

**Phase 1:** Unknown and unmonitored  
**Phase 2:** Known, but unmonitored.  
**Phase 3:** Pandemic response capability developed and deployed.

## Why sequencing had a limited impact on COVID-19

### The state of the art: PCR testing

Currently, our systems of outbreak monitoring are far from pandemic-proof. Disease response centers monitor spikes in patients with novel symptoms. This monitoring relies largely on reporting by an “astute physician” who notices unusual signs of an illness (a challenging task given the similarity of symptoms across a wide range of pathogens) and on self-reporting by hospitals, with guidelines varying in countries across the world[¹](https://www.zotero.org/google-docs/?EzO1X2). Therefore, we are likely to **only notice an outbreak once a critical mass of infections has taken place.** At this point of the exponential growth typically exhibited by pandemic-capable pathogens, an outbreak is substantially more difficult to contain than it is at earlier phases.

Once a suspected novel virus has been identified, it may be isolated and sequenced. In the case of SARS-CoV-2, known viruses were first ruled out through antigen kits and subsequently by qPCR. Only later analysis by metagenomic sequencing identified a novel viral strain.[²](https://www.zotero.org/google-docs/?AQxYU8)

To understand the limitations of this model, we need to consider the current state of the art. During COVID-19, polymerase chain reaction (PCR) tests became well-known tools for identifying the presence and quantity of known pathogens in a sample. PCR testing is correctly thought of as the gold standard because of its high sensitivity for known pathogens. Furthermore, we have experience with scaling PCR-based testing and sample-to-answer devices with relatively simple workflows have become widespread in clinics around the world.

While the majority of PCR tests target a single pathogen, PCR testing is scalable for high-throughput analysis and can run multiplexed panels of over 40 targets with run times under 60 minutes. New approaches to DNA synthesis (enzymatic approaches) could potentially help ramp up and distribute the production of qPCR kits once a novel threat has been identified.

However, PCR testing faces important limitations for detecting and containing potential pandemics quickly:

- **Detection of unknown pathogens:** PCR tests rely on previously identified fragments of pathogenic nucleic acid (primers) for detection, and therefore by definition cannot identify a novel pathogen such as SARS-CoV-2.

- **Development timeline:** Developing new primers for PCR-based testing and monitoring can take weeks or months, which introduces a substantial time lag before mass testing becomes practical, even if approval of such a test is expedited under EUA.

We can consider in more detail the delay this lack of technological preparedness caused in COVID-19.

The SARS-CoV-2 genome was made publicly available in January 2020, more than two months after the first human transmission. For current diagnostic approaches, this is a significant issue. Each new virus requires a new test to be developed, approved, and deployed. When potentially hundreds of millions of tests are required, this is a huge logistical issue.

In the case of COVID-19, it took more than 4 months for 1 million tests to be performed in the US and 9 months to deploy 100 million tests[⁷](https://www.zotero.org/google-docs/?s9uX3H). Logistical and regulatory issues, therefore, limit our ability to engage in “track and trace” operations allowing the pandemic to proceed largely unmonitored.

### Metagenomic sequencing

In order to remove the long ramp-up associated with kit deployment, we either need kits that can be more rapidly produced or that are pathogen-agnostic. The ability to stockpile tests without the need to predict the pathogen they will be used for is a distinct advantage.

In contrast to qPCR, MGS can in principle detect any pathogen, viral or bacterial, in a clinical sample. In addition, in a world with ubiquitous testing of respiratory infections by MGS, a time lag between identification of a new pathogen and test development would be nearly removed. 

> An attractive option is therefore to provide a **universal diagnostic for respiratory (and other) conditions** based on MGS. In this scenario, a symptomatic individual would visit a primary care physician to be evaluated. The physician could perform a MGS-based test to detect both known and unknown pathogens, which would provide a valuable diagnostic to guide care. For example, an anterior nasal swab test could determine if a patient had a viral, bacterial or fungal infection, determine the strain of pathogen, and ideally identify any anti-microbial resistance genes to guide treatment. Essentially, this would provide an enhanced full respiratory diagnostic panel for the cost of a Flu/RSV/COVID qPCR kit. When unknown RNA or DNA is detected, the information could be sent to a central (likely cloud-based) monitoring center, providing a pandemic early warning system.

Despite these clear advantages over traditional approaches, sequencing-based diagnostics have not gained traction during COVID-19 beyond use for tracking variants that give rise to new strains. There are two strong factors which have prevented adoption:

- **Cost:** qPCR costs less than $5 where sequencing costs at least \$100 per sample/run.

- **Market:** no metagenomic sequencing assay is currently clinically validated and approved as a diagnostic for infectious disease.

The value to both the user and clinicians of metagenomic sequencing-based diagnostics therefore needs to be made clear. Among other considerations, the cost of such a diagnostic test needs to be low enough to allow it to be economically performed. We discuss these requirements in the following chapter.

[^1]: We justify this in “[Sensitivity](https://sequencing-roadmap.org/sensitivity)”
