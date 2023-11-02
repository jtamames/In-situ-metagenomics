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

And also other reccomendations:

- [Powering the system](#Powering-the-system)
- [Other equipment](#Other-equipment)

## Sample preparation

Follow your usual protocol for preparing samples. Rock samples must be grinded to a fine powder. Water samples must be filtered through a column to keep the adequate fraction.

## DNA extraction

Equipment needed:

![spinner](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/d95d9d45-9de7-45b9-af72-16a5d26b1a9c)&nbsp;&nbsp;
![vortex](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/3ebcf067-ae83-4744-98ae-3ec98ab75719)&nbsp;&nbsp;
![centri](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/f327d3d4-500e-4df8-937e-61405161685c)


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Spinner&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Vortex&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Mini centrifuge


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

![qubit](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/de59acda-7b94-4bd7-83fd-e7f069a08132)

Qubit4 Fluorometer

We use the High Sensitivity Assay. Find the full protocol [here](https://assets.thermofisher.com/TFS-Assets/BID/manuals/MAN0017210_Qubit_4_Assays_QR.pdf)

As you need to load 400 ng on the nanopore flow cell, and you will put 10 &mu;l of DNA solution 
when preparing the library, you would need a concentration of 40 ng/&mu;l, at least.

## DNA purification and concentration

We use Omega Mag-Bind TotalPure NGS Beads. The purpose of this step is:

-To remove possible impurities in the DNA solution that can harm the flow cell afterwards

-To increase the ratio of long DNA sequences

For this, we will use a magnetic rack like this one:

![rack](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/4499d363-1f61-42fe-b8e6-336b5151a92d)

Mini magnetic rack (2 tubes)

The full protocol can be found [here](https://es.vwr.com/assetsvc/asset/es_ES/id/23373537/contents/m1378-mag-bind-total-pure-ngs-online.pdf)

It is advisable to determine DNA concentrations before this step, to estimate the performance of the purification. 

It is important to determine the ratio magnetic beads/DNA soultion to be used. The higher this ratio, the most exhaustive the separation, meaning less quantity of DNA, but longer sizes. Ideally we want longer DNAs, but if it was heavily fragmented in the extraction step, we could lose most of it.
In our experience, good ratios range from 0.8 to 1.4 x. One possible approach is making one pass at lower ratios, quantify the concentration, and repeat with higher ratios if the concentration is enough.

Concentration can be done eluting in a smaller volume than the original. Tipically you would elute in 50 μl (step 17 in DNA extraction). Now, in the final step of the purification, you can elute in a smaller volume to concentrate the DNA. The minimum advisable volume is around 15 μl (you will need 10 μl for the library, plus a few μl for quantification)

## Library preparation

New equipment needed:

![miniPCR](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/cb8dd38a-0402-495f-8017-1e51c99370e6)

Mini-thermocycler

In this step we create the DNA library for sequencing in the minION device. There are different ways to prepare DNA libraries for usage in ONT sequencers. We use the [Rapid Barcoding kit](https://store.nanoporetech.com/eu/rapid-barcoding-kit.html), because of its simplicity and quickness. Little manipulation is needed. In brief, the protocol for creating the library includes fragmentation with a transposase that fragments DNA and inserts barcodes in the tips of the DNA sequences. Then, Rapid Sequencing Adapters are then added to the tagged ends, and the library is ready for sequencing. The full protocol can be found [here](https://community.nanoporetech.com/docs/prepare/library_prep_protocols/rapid-barcoding-sequencing-sqk-rbk004/v/rbk_9054_v2_revaf_14aug2019)

CAVEATS:

- A mini thermocycler is needed because the transposase in the kit needs to be inactivated at 80&deg; C. We use [this one](https://www.minipcr.com/product/minipcr-mini8-thermal-cycler) because of its portability, usability, bluetooth connection, and because it is really cute (but beware, it is also very sensitive and stops working in the cold).
- Be efficient if the transposase step. Do not let it to act longer than one minute. Likely, we already have a fragmented DNA because of the extraction step. If the transposase acts wildly, you will end with very short DNAs that will compromise the sequencing, because the adapter binds less efficiently to short sequences. Have everything ready for inactivating the transposase before adding it.
- The thermocycler can be replaced by a thermal bath with hot water. We have succesfully tried this is some experiments. You would need three small pots. Fill one with hot water that you keep in a thermo, or bring an electric kettle, or a portable water heater. Heat the water to 85&deg; C, checking the temperature with a digital thermometer. Fill a second pot with water at 35&deg; C, using the same procedure. And finally fill the other pot with water and ice. After adding the transposase, take the tube with tweezers, incubate it by submerging the tube in the 35&deg; C bath, then pass it to 80&deg; C, and finally cool it down in the water/ice pot.
- The Rapid Barcoding kit comes with 12 barcodes, allowing multiplexing of different samples in the same library. Additional barcodes can be purchased if needed.
- The binding of adapters to sequences is rather fragile. After adding the adapters, be very gentle in all subsequent manipulations (no vortexing of course, mix solutions by pippeting up and down very carefully)

## MinION sequencing

New equipment needed:

![minion](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/3cb89c4f-147c-46d4-aba6-81468af3e379)

MinION device and laptop computer

First, install [MinKNOW](https://nanoporetech.com/about-us/news/introducing-new-minknow-app) in the laptop. This is the ONT software managing the MinION. Almost any laptop is suitable for managing the sequencing, altough a high-performance one is advisable. RAM memory is critical for the subsequent analysis, no less than 16 Gb is reccomended, and the more the better. Number of cores is also important, I would reccomend eigth. And you would need storage capacity for storing results. Take into account that MinKNOW will require a minimum amount of storage to start the sequencing (around 100 Gb). If the laptop has a GPU, much better, because this will increase a lot the basecalling performance.

MinKNOW needs internet connection because it downloads some data at the beginning of the run. If you are planning to do sequencing in the wild, you will need to set up MinKNOW to work wth no internet connectivity. In order to change your Linux version of MinKNOW to the offline version, do the following:

    1.Install latest version of the software.
    2.Disable the WiFi to prevent connection after restarting.
    3.Shutdown the computer
    4.Remove the ethernet cable
    5.Power on the computer
    6.Open a terminal and run the following commands
        sudo /opt/ont/minknow/bin/config_editor --filename /opt/ont/minknow/conf/sys_conf --conf system 
        --set on_acquisition_ping_failure=ignore
    7. Restart the MinKNOW service by running the following commands:
        sudo systemctl daemon-reload
        sudo systemctl enable minknow
        sudo systemctl start minknow
    8.Shutdown the computer
    9.Power on the computer

For actually running the sequencing, you will need a MinION flow cell or Flonge. The latter is much less expensive, but also is single-use and provides less amount of sequencing because of its reduced number of pores.

Check the flow cell as soon as it arrives. It is needed to start the experiment, and you will avoid nasty surprises (sometimes the cells are damaged and ONT will not replace them if they are expired).

A Priming Kit is shipped with the Rapid Barcoding kit. You need it to prime the flow cell. This is usually done simultaneously to library preparation. The protocol can be found [here](https://community.nanoporetech.com/docs/prepare/library_prep_protocols/rapid-barcoding-sequencing-sqk-rbk004/v/rbk_9054_v2_revaf_14aug2019/priming-and-loading-the-sp?devices=minion)

Then proceed to load the library on the flow cell, following the same protocol above. 

Open the MinKNOW application and click on the "Start sequencing" option. Navigate through the menus following [this protocol](https://community.nanoporetech.com/docs/prepare/library_prep_protocols/experiment-companion-minknow/v/mke_1013_v1_revcy_11apr2016). The options are very straightforward, and very few options need to be adjusted. Set run length to 72 hours (you can always stop it sooner). Set the output to gzip compressed fastq files. You can also change the time between MUX scans if you want to check the flow cell status more or less often.

Check the sequencing progress using the MinKNOW's GUI. Several informations are available, for isntance a plot of the channel states, like this:

![stats](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/34646382-d3f8-4f06-b41d-dd3f4761f6d3)

Each channel is a grouping of several pores, and the status show what they are doing. The "Strand" ones are the channels that are sequencing a DNA strand. "Single pore" are empty channels. And "Adapter" are the ones that are attached to adapters but not actually sequencing. You would like to see few "Single pore" channels. If you see many, there is little DNA in the flow cell. Should you see many "adapter" channels, that means that there is plenty of free adapters, again because DNA is scarce, or because the adapters did not bind properly to DNA strands. The latter can happen because of small lenghs of the DNAs, probably prointing to excesive fragmentation during the DNA extraction or the preparation of the library.

Let the sequencing proceed until you have enough number of sequences, or until you see that the cell ran out of DNA (you will notice a decrease in the number of "strand" channels). In the latter case, you always can load more library in the cell, if you have prepared excess of it.

## Bioinformatic analysis

Now, we would like to have information about the taxa and functions encoded in the genes in the metagenome, and calculate abundances for each. For this, you will need the SqueezeMeta software. Install it following the instructions in the [repo](https://github.com/jtamames/SqueezeMeta)

SqueezeMeta is a software pipeline grouping all the tools needed for analyzing a metagenome. It has been designed to run in scarce computational resoulrces, even in a laptop.

After stopping the sequencing, locate the fastq.gz sequence files produced, and create a samples file as indicated [here](https://github.com/jtamames/SqueezeMeta#the-samples-file). As these are minION reads, unpaired, you don´t need to specify a "pair2" file.

SqueezeMeta includes modes for working with long reads coming from MinION or PacBio sequencers. An explanation of these modes can also be found in the SqueezeMeta [README](https://github.com/jtamames/SqueezeMeta#10-working-with-oxford-nanopore-minion-and-pacbio-reads) and [manual](https://github.com/jtamames/SqueezeMeta/blob/master/SqueezeMetaManual_1.6.3.pdf). 

You can opt for two kind of analysis:
- Relying on assemble the sequences: The way of running this analisis is explained [here](https://github.com/jtamames/SqueezeMeta#execution). For having good results with this you will need sufficient DNA sequences for the assembly, otherwise the assembly will be very small and incomplete. How much you need is difficult to tell, because it depends of the richness and diversity of the microbiome. You can check the completeness of the assembly using the read mapping percentage. Should you see this percentage is low, it means that most reads are not represented in the assembly. In this case you can switch to:
- Analyzing the reads directly: In this case, SqueezeMeta will forget about the assembly and will work with reads. This has the advantage of being more complete, since all reads are taken into account (not only the assembled ones, as when using an assembly). But also the drawback of being much slower. SqueezeMeta includes the 'sqm_longreads.pl' program for running this analysis. Check the [SqueezeMeta manual](https://github.com/jtamames/SqueezeMeta/blob/master/SqueezeMetaManual_1.6.3.pdf) for details 

When few hours later the SqueezeMeta run has finished, you can load them into the SQMtools R library that is included in the SqueezeMeta pipeline, for examining the results and doing the appropriate statistics, as you can see in [this tutorial](https://github.com/jtamames/SqueezeMeta/wiki/Using-R-to-analyze-your-SQM-results)

## Powering the system

If you are planning to use this system outdoors, you would need a power supply for running all the equipment above.

We are using this very nice 200 W [portable batteries](https://www.uking-online.com/product/uking-portable-power-generator-222wh-60000mah-with-dc-ac-inverter-charged-by-solar-panel-wall-outlet-for-solar-generator-outdoor-camping-travel-emergency-backup):

![battery](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/eedba661-3e79-4c58-a718-c7c722e59943)


Their 60000mAh are providing us with several hours of autonomy. One of them is capable to support all the setting above for a full experiment, altough you will want to bring two for backup purposes. Another good feature is that they are rather cheap, and ligther than you expect (2.4 Kg).

Take into account that, in cold conditions, all bateries will be drained very quickly, and these are not the exception. It will be needed to isolate these in some container that can be heated.

## Other equipment

Some other stuff that you will find adequate (and miss if you didn´t bring them):

- A small tent: You need some shelter, for you and for the equipment. The main requirements are:
  - Stable
  - tall enough to allow being sitted inside
  - ligth weigth

  We usually take two with us, one for working, and a second for keeping stuff and resting

- A small, portable camping table: Stable and ample enough to fit instruments and work on it.
- A ligth camping chair. This and the table are a must.
- A small power strip. We connect it to the battery, just for having all instruments plugged at once.
- A container for residues: Don´t forget this, you will produce some resudies that need to be disposed properly.


- Thermal isolated containers: some reactives (and flow cells) need to be in cold storage. We use a portable camping fridge like this one, and fill it with ice blocks.
  
![fridge](https://github.com/jtamames/In-situ-metagenomics/assets/34687997/8c067762-5ab4-4ca3-a256-36e4b76f0bd5)

  In case you are working in cold conditions, you will find interesting the use of the small hand warmer that you can see in the picture. Putting two of these in the containers helps to keep the temperature warm enoughfor devices such as the batteries or the MinION sequencer, that are sensitive to cold.

Finally, you will need a backpack or similar to carry all this. We pack everything in a 70L backpack. Final weigth is around 15 Kg, so don´t forget to enrol your strongest student in the project!





