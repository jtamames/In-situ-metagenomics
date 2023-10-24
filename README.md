# In-situ-metagenomics
A protocol for perrforming sequencing experiments directly in the field

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

17. Add 50–100 μl of Solution C6 to the center of the white filter membrane.

18. Centrifuge at 15,000 x g for 1 min. Discard the MB Spin Column.

CAVEATS:

-If the portable centrifuge cannot provide the requested g, try increasing centrifugation time.

-The kit relies on a bead-beating step to mechanically lyse cells. Be gentle with that step, since it could lead to extensive DNA fragmentation, hampering library preparation afterwards.

## DNA purification and concentration

We use Omega Mag-Bind TotalPure NGS Beads. The purpose of this step is:

-To remove possible impurities in the DNA solution that can harm the flow cell afterwards

-To increase the ratio of long DNA sequences

For this, we will use a magnetic rack like this one

![rack](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/ed689cfd-9d6b-41d5-a67b-302dee21cd80)

## DNA quantification

Equipment needed:

![qubit](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/44301144-ca1a-4905-8137-ca8b2c5022d3)
Qubit4 Fluorometer

We use the High Sensitivity Assay. Find the full protocol [here](https://assets.thermofisher.com/TFS-Assets/BID/manuals/MAN0017210_Qubit_4_Assays_QR.pdf)

As you need to load 400 ng on the nanopore flow cell, and you will put 10 &mu;l of DNA solution 
when preparing the library, you would need a concentration of 40 ng/&mu;l, at least.


