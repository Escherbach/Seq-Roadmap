# Single-molecule optical approach

What causes the relatively high COGS for Illumina?

A large part of the answer comes down to a fairly complex reagent cartridge. Plastics and the reagents themselves likely cost very little. However, Illumina rquiresnreagents for cluster generation (bridge amplification), cleavage reagents, second read reagents etc. and it is hard to imagine how any of these components could be removed in this platform. Asa result, it is difficult to imagine how a 14 component reagent cartridge, could be optimized below $50.

![b1cb471d-d5d1-4386-9928-6a2149f2d5df_3374x932.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fb1cb471d-d5d1-4386-9928-6a2149f2d5df_3374x932.png)

Therefore, we may want to remove all this complexity and ideally remove the fluidic system completely. This would not only simplify the consumable, but also ::result in a simpler, smaller instrument which does not require field support::. A broken instrument of this sort could be sent back for consumer support much like an iPhone.

## Sequencing Approaches

Another feasible approach one could take is single-molecule sequencing-by-synthesis.

It is not surprising why this approach has not become attractive in a research setting. The three main reasons are:

- **Throughput.** ::The approach would likely be limited to:: [::1M reads::](craftdocs://open?blockId=3D7D9365-572A-4091-8F62-FEF86C0A4EDB&spaceId=825034bc-4212-0075-f58a-751af8809e0c):: over the fixed imaging region::. You could potentially push this further, for example once everything is bleached out, you could imagine adding more sequencing templates.
- **Read length.** Photodamage to templates is going to limit read length. Helicos-like sequencing platforms have previously reached reads in the [33 to 53bp range](craftdocs://open?blockId=3D7D9365-572A-4091-8F62-FEF86C0A4EDB&spaceId=825034bc-4212-0075-f58a-751af8809e0c).
- **Error rates.** Without further nucleotide development probably in the <5% range.

Our argument, supported in the appendix, can be summarized as follows:

- Simple sample preparation. Previous approaches typically took advantage of a cyclic chemistry. As noted before, this should be avoided if we want to keep sample preparation simple. However, single-molecule optical sequencing can work without cyclic chemistries.
- Low cost of goods. While optical instrumentation used to be prohibitively expensive (>$20,000 for a camera) in the days of Helicos, today, sufficient system can be assembled for <$400.
- Sufficient sensitivity for respiratory viruses.

![0d1d64c7-96e5-4137-a33a-3ef3dcc35adf_1776x744.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F0d1d64c7-96e5-4137-a33a-3ef3dcc35adf_1776x744.png)

### Cyclic chemistry and photobleaching

   - Rather than cleaving dyes, one can remove them with photobleaching. Prior work demonstrates that this can be done in a single-molecule optical context.
   - There’s [prior work where photobleaching has been used to remove signal](https://www.pnas.org/content/pnas/100/7/3960.full.pdf) for single molecule sequencing. But the Reticula approach is slightly different. In prior work, photo-bleaching was taken to completion before flowing in new nucleotides.
   - This does limit us to a single observation area but, in the context of a clinical diagnostic, the resulting simplification of sample prep is worth the trade-off.

![872688ca-cc7b-4434-9286-26a153f1a183_1800x750.png](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F872688ca-cc7b-4434-9286-26a153f1a183_1800x750.png)

### Signal processing

- The result will be a sequencing approach where we see stepwise increases in emission intensity when nucleotides are incorporated, and stepwise decreases when bleaching occurs.
- To determine which nucleotide was incorporated we can use one of two approaches. Either each nucleotide is labeled with a dye that emits at a different wavelength (the traditional approach) or we select dyes such that they different in emission strength at a single wavelength.

The advantage of the second approach is that we only need a single filter/camera, further simplifying the instrument.

The result will be a somewhat convolved “steppy” signal. Upward steps are incorporation events, downward steps are bleaching events. Bleaching events can occur in any order, but incorporation events will obviously occur in template order.

However, both incorporation and bleaching events give us information about the template being sequenced. A Hidden Markov Model can be used to combine all this information and find the most probable underlying template sequence:

![7b4a95e7-45e7-43f2-97dc-33365b5f368f_1878x890.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F7b4a95e7-45e7-43f2-97dc-33365b5f368f_1878x890.png)

The system described above doesn’t need any fluidics. You can imagine for example that your polymerase and nucleotides might be directly embedded in the flowcell. When the sample is added, it could wick into an imaging area and the polymerase would start incorporating bases. A fixed camera would then be used to observe incorporations in real time.

## Optical System

To make this work we need a cheap platform for performing single molecule experiments. Back when Helicos was around, this wasn’t really possible. And even today most research users use SCMOS cameras which cost $20000++.

But it turns out consumer grade cameras have got a lot better:

![ccf51f8e-31e3-411e-8933-76e403de408e_1806x890.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fccf51f8e-31e3-411e-8933-76e403de408e_1806x890.png)

For [my experiments I’ve been using IMX178 and IMX174](https://41j.com/blog/2021/04/single-dye-experiments-on-a-genome-analyzer/) cameras. These cameras are designed for low light security applications. They work well and cost <$300 in single units.

To observe single molecule events, we really need some kind of TIRF setup. Most current research experiments use objective style TIRF. The problem here is that high NA TIRF objectives are expensive ($5000). So we don’t want to do that. Instead we use prism style TIRF.

Rather handily this was the approach used in the original Solexa Genome Analyzer. So my prototypes repurpose this optical system:

![bcc2043d-dbe7-441d-b377-3aa1a7e154cb_2822x2727.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fbcc2043d-dbe7-441d-b377-3aa1a7e154cb_2822x2727.png)

This setup has allowed me to prove out the optical approach and obtain single molecule photobleaching data:

![7265110e-37ec-4958-bb81-942ab08a8d8c_2330x1574.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F7265110e-37ec-4958-bb81-942ab08a8d8c_2330x1574.png)

I’ve also sourced cheap fused-silca prisms, lasers and objectives from Shenzhen. Overall, this suggests that it should be possible to build a very cheap, small instrument:

![0d1d64c7-96e5-4137-a33a-3ef3dcc35adf_1776x744.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F0d1d64c7-96e5-4137-a33a-3ef3dcc35adf_1776x744.png)

The one issue with prism TIRF (as anyone who has used a Genome Analyzer will know) is that it’s a bit messy. This is because you need do put oil on the prism to couple it to the flowcell. You may be able to get round this by using a plastic prism embedded into the flowcell, the issue here is that most plastics are somewhat autofluorescent. Some plastics however, [are better than others](https://pubs.rsc.org/en/content/articlelanding/2005/LC/b508288a). And you maybe able to find one where this isn’t an issue.

