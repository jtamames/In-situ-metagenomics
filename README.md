# In-situ-metagenomics
This is a protocol for performing sequencing experiments directly in the field. A full paper describing the application of this protocol can be found in [BioRxiv](https://www.biorxiv.org/content/10.1101/2023.01.25.525498v1)

We have been able to run this full protocol in less than 24 hours, in several instances.

The protocol comprises several steps:

- [Sample preparation](#Sample-preparation)
- [DNA extraction](#DNA-extraction)
- [DNA quantification](#DNA-quantification)
- [DNA purification/concentration](#DNA-purification-and-concentration)
- [Library preparation](#Library-preparation)
- [MinION sequencing](#MINion-sequencing)
- [Bioinformatic analysis](#Bioinformatic-analysis)

## Sample preparation

Follow your usual protocol for preparing samples. Rock samples must be grinded to a fine powder. Water samples must be filtered through a column to keep the adequate fraction.

## DNA extraction

Equipment needed:

![centri](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/646fcb28-f845-4a64-9807-782cbf82dff0)
Centrifuge yielding 16.000 g

![spinner](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/5b760214-6524-45f9-9603-b3334fad3fbb)
Spinner

![vortex](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/7dad732d-bcb4-4626-ab5c-5786e9a4220a)
Vortex

We use Qiagen's DNeasy PowerSoil Pro Kit for extracting DNA, because it does not imply heating steps, which is best for us. 

A full protocol can be found [here](https://www.qiagen.com/us/Resources/ResourceDetail?id=3d576814-4f1e-4e26-9c94-57d5dc2bb60a&lang=en). A summary follows:

1. Spin the PowerBead Pro Tube briefly to ensure that the beads have settled at the bottom.
Add up to 250 mg of sample and 800 μl of Solution CD1. Vortex briefly to mix.

3. Secure the PowerBead Pro Tube horizontally on a Vortex Adapter for 1.5–2 ml tubes Vortex at maximum speed for 10 min.

4. Centrifuge the PowerBead Pro Tube at 15,000 x g for 1 min.

5. Transfer the supernatant to a clean 2 ml Microcentrifuge Tube

6. Add 200 μl of Solution CD2 and vortex for 5 s.

7. Centrifuge at 15,000 x g for 1 min at room temperature. Avoiding the pellet, transfer up to 700 μl of supernatant to a clean 2 ml Microcentrifuge Tube 

8. Add 600 μl of Solution CD3 and vortex for 5 s

9. Load 650 μl of the lysate onto an MB Spin Column and centrifuge at 15,000 x g for
1 min.

10. Discard the flow-through and repeat step 8 to ensure that all of the lysate has passed
through the MB Spin Column.

11. Carefully place the MB Spin Column into a clean 2 ml Collection Tube

12. Add 500 μl of Solution EA to the MB Spin Column. Centrifuge at 15,000 x g for
1 min.

13. Discard the flow-through and place the MB Spin Column back into the same
2 ml Collection Tube.

14. Add 500 μl of Solution C5 to the MB Spin Column. Centrifuge at 15,000 x g for 1 min.

15. Discard the flow-through and place the MB Spin Column into a new 2 ml Collection Tube

16. Centrifuge at up to 16,000 x g for 2 min. Carefully place the MB Spin Column into a
new 1.5 ml Elution Tube 

17. Add 50 μl of Solution C6 to the center of the white filter membrane.

18. Centrifuge at 15,000 x g for 1 min. Discard the MB Spin Column.

CAVEATS:

- If the portable centrifuge cannot provide the requested g, try increasing centrifugation time.

- The kit relies on a bead-beating step to mechanically lyse cells. Be gentle with that step, since it could lead to extensive DNA fragmentation, hampering library preparation afterwards.
  
- If you expect the DNA concentration in your samples to be low, you can use several tubes for steps 1-8, and then pass them through a single elution column. In this way you can increase the amount of DNA retained in the column.

## DNA quantification

New equipment needed:

![qubit](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/44301144-ca1a-4905-8137-ca8b2c5022d3)
Qubit4 Fluorometer

We use the High Sensitivity Assay. Find the full protocol [here](https://assets.thermofisher.com/TFS-Assets/BID/manuals/MAN0017210_Qubit_4_Assays_QR.pdf)

As you need to load 400 ng on the nanopore flow cell, and you will put 10 &mu;l of DNA solution 
when preparing the library, you would need a concentration of 40 ng/&mu;l, at least.

## DNA purification and concentration

We use Omega Mag-Bind TotalPure NGS Beads. The purpose of this step is:

-To remove possible impurities in the DNA solution that can harm the flow cell afterwards

-To increase the ratio of long DNA sequences

For this, we will use a magnetic rack like this one:

![rack](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/ed689cfd-9d6b-41d5-a67b-302dee21cd80)
Mini magnetic rack (2 tubes)

The full protocol can be found [here](https://es.vwr.com/assetsvc/asset/es_ES/id/23373537/contents/m1378-mag-bind-total-pure-ngs-online.pdf)

It is advisable to determine DNA concentrations before this step, to estimate the performance of the purification. 

It is important to determine the ratio magnetic beads/DNA soultion to be used. The higher this ratio, the most exhaustive the separation, meaning less quantity of DNA, but longer sizes. Ideally we want longer DNAs, but if it was heavily fragmented in the extraction step, we could lose most of it.
In our experience, good ratios range from 0.8 to 1.4 x. One possible approach is making one pass at lower ratios, quantify the concentration, and repeat with higher ratios if the concentration is enough.

Concentration can be done eluting in a smaller volume than the original. Tipically you would elute in 50 μl (step 17 in DNA extraction). Now, in the final stpe of the purification, you can elute in a smaller volume to concentrate the DNA. The minimum advisable volume is around 15 μl (you will need 10 μl for the library, plus a few μl for quantification)

## Library preparation

New equipment needed:

![miniPCR](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/bf925ca1-1c5b-44d6-b117-9fff1b454f90)
Mini-thermocycler

In this step we create the DNA library for sequencing in the minION device. There are different ways to prepare DNA libraries for usage in ONT sequencers. We use the [Rapid Barcoding kit](https://store.nanoporetech.com/eu/rapid-barcoding-kit.html), because of its simplicity and quickness. Little manipulation is needed. In brief, the protocol for creating the library includes fragmentation with a transposase that fragments DNA and inserts barcodes in the tips of the DNA sequences. Then, Rapid Sequencing Adapters are then added to the tagged ends, and the library is ready for sequencing. The full protocol can be found [here](https://community.nanoporetech.com/docs/prepare/library_prep_protocols/rapid-barcoding-sequencing-sqk-rbk004/v/rbk_9054_v2_revaf_14aug2019)

CAVEATS:

- A mini thermocycler is needed because the transposase in the kit needs to be inactivated at 80&deg; C. We use [this one](https://www.minipcr.com/product/minipcr-mini8-thermal-cycler) because of its portability, usability, bluetooth connection, and because it is really cute (but beware, it is also very sensitive and stops working in the cold).
- Be efficient if the transposase step. Do not let it to act longer than one minute. Likely, we already have a fragmented DNA because of the extraction step. If the transposase acts wildly, you will end with very short DNAs that will compromise the sequencing, because the adapter binds less efficiently to short sequences. Have everything ready for inactivating the transposase before adding it.
- The thermocycler can be replaced by a thermal bath with hot water. We have succesfully tried this is some experiments. You would need three small pots. Fill one with hot water that you keep in a thermo, or bring an electric kettle, or a portable water heater. Heat the water to 85&deg; C, checking the temperature with a digital thermometer. Fill a second pot with water at 35&deg; C, using the same procedure. And finally fill the other pot with water and ice. After adding the transposase, take the tube with tweezers, incubate it by submerging the tube in the 35&deg; C bath, then pass it to 80&deg; C, and finally cool it down in the water/ice pot.
  
-The Rapid Barcoding kit comes with 12 barcodes, allowing multiplexing of different samples in the same library. Additional barcodes can be purchased if needed.
