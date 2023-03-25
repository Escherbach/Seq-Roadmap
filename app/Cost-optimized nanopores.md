# cost-optimized nanopore array fabrication

As previously noted, Oxford Nanopore's lower-end nanopore sequencer, the Flongle, may be the closesr device from those currently available to meeting our product progile specifications. It comfortably meets the throughput and time to answer requirements. Sample preparation is still complex but there do not appear to be any reasons why a nanopore sequencer could not be coupled with a low-cost reagent cartridge along the lines we propose. However, its COGS (~$90) of the Flongle is still at least and order of magnitude higher than our goal of less than $10.

To our knowledge, there is no publicly available information on the manufacturing process that would aid a more grounded estimate of the cost of nanopre fabrication. In an appendix, we review a [patent from Oxford Nanopore](https://patents.google.com/patent/US20220023819A1) covering array fabrication approaches and use it to estimate how cheap a Flongle-type device could be if manufactured at scale.



### Electrodes

The patent suggests that [Silex](https://silexmicrosystems.com) were used to fabricate electrodes on a 6 inch Si wafer. [Other patents](https://patentimages.storage.googleapis.com/a2/77/fa/3972fda2f2c3db/US10549274.pdf) give a better sense of the wafer structure:

![38630225-1250-42c2-830e-9d39a49d9dcf_1300x706.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F38630225-1250-42c2-830e-9d39a49d9dcf_1300x706.png)

Here we have platinum electrodes with through wafer interconnects. This allows the electrodes on the top surface to be routed through the substrate and out of the bottom of the wafer where they can be bonded to an ASIC (in the case of the MinION) or pins (Flongle). This looks rather like a [TSV (Through Silicon Via) process](https://www.youtube.com/watch?v=-egYoxajTz0).

The use of Platinum perhaps explains why a MEMS fab (Silex) is being used here rather than a more standard process, where typically [copper or aluminum](https://semiengineering.com/breaking-the-2nm-barrier/) would be used on metal layers.

Nanopore experiments in academia usually use silver electrodes, however as noted silver is “difficult to incorporate in a silicon wafer manufacturing process due to its tendency to undergo oxidation on exposure to light, air and high temperatures”. So this isn’t a good option here.

Patents also describe an optional electrode spike, but while Silex have some cool [patents around fabricating micro-needles](https://patents.google.com/patent/US8637351B2), this seems challenging, and doesn’t seem to be mentioned elsewhere in the patent.

![de7f1eca-8b7e-467f-8eb3-cc22e167462a_542x325.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fde7f1eca-8b7e-467f-8eb3-cc22e167462a_542x325.png)

### Membranes and Structures

The substrate described above, contains the basic electrode structure. Droplets need to added to the array into which nanopores will be inserted. These droplets need to be confined above electrode. A structure sits above the electrode to enable this.

These structures are formed using SU-8 (Seed layer) and TMMF 2030 dry-film resist (Pillar structure):

![5e64f403-cc7e-4c81-bb9f-8cb15d5ba184_1279x699.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F5e64f403-cc7e-4c81-bb9f-8cb15d5ba184_1279x699.png)

Structure from [this patent](https://patents.google.com/patent/US20220023819A1) and optical image from [this patent](https://patentimages.storage.googleapis.com/24/b5/ed/cc4e29f1e0e297/US10760114.pdf)

### Well Sizes and Pore Lifetime

The patents notes that the experiment/pore lifetime is related to the volume of the droplet. The graph below would suggest that a MinION (with a 72h run time) uses droplets in the 175 micron range:

![7849f58d-e6d6-44be-8eb9-9f4fd92400d9_638x453.jpeg](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F7849f58d-e6d6-44be-8eb9-9f4fd92400d9_638x453.png)

It also suggests that if you try to fit more pores onto a chip, and in doing so reduce droplet size, flow cell lifetime will decrease. This may limit options in terms of increasing pore density to push throughput.

### How Much does this all cost?

The [Flongle array appears](https://www.flickr.com/photos/theworldfishcenter/49714974428/in/photostream/) to be somewhere in the region of 10mm square. This may be somewhat limited by mechanical constraints, as it seems like 126 wells should fit on a substrate less than a quarter of this size easily.

Existing MEMS fabrication capacity for the processes used (from [pureplay MEMS fab](https://silexmicrosystems.com)s) is probably somewhat limited. This limited supply likely contributes significantly to this $20 cost per device.

One route to a low cost per device could therefore be to build out specialized fab capacity. For the kinds of point-of-care devices we have analyzed in the report we would be looking at >1M units a month. Building out such a fab would likely be very expensive: at least $200M, likely closer to $1B But with such a facility, it seems at least plausible that you one could reach a single digit dollar COGS, possibly as low as $1-2.

### Other approaches

The silicon substrate array approach seems to be most appropriate for scaling out arrays to 1000s or 10000 pores. But if we’re content with the 126 pores on a Flongle, might other approaches be a better fit?

One approach might be to fabricate silver electrodes on printed circuit boards directly. The Italian company Elements have demonstrated this in their [single channel solid state nanopore systems](https://elements-ic.com/wp-content/uploads/2019/07/eNPR-%E2%80%93-Nanopore-Chip-assembly-and-measurement-instructions.pdf):

Silver immersion PCBs are [readily available](https://www.pcbtrain.co.uk/blog/how-should-i-keep-my-pcbs-with-a-silver-finish) and not particularly expensive. Silver (AgCl) electrodes are pretty much the standard way of creating electrodes in ion channel experiments. Silver, however, oxidizes relatively easily, making it less desirable in a semiconductor fabrication environment.

However, on a PCB, this should not be as much of an issue. These boards can support features down to about 125 microns. Allowing a square millimeter for each well, we can still fit 100 wells into a 10 square millimeter PCB. Boards of this size can be ordered for ~50 cents, with next-day turnaround. Much lower prices are likely available.

Like the Flongle, this would need to interface with an external ASIC. It seems plausible that [off the shelf current sense amplifiers](https://41j.com/blog/2018/08/ddc112-board-design-bring-up/) might work for this. Parts are available, which support up to [256 channels per chip](https://www.ti.com/product/DDC2256A#tech-docs). Failing that, a custom ASIC would also need to be developed.

