# RNA seq technology

### 2020 our new tech

方案一：发展低bias、低成本、高通量的测序方法

in liquid biopsy

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription+ UMI, secondstrand complementary DNA (cDNA) synthesis, adapter ligation, and PCR amplification 

i-SMART validation

方案二：实现更快速、具有组分特异性的测序流程

in liquid biopsy

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription, secondstrand complementary DNA (cDNA) synthesis, ~~adapter ligation~~, and PCR amplification

1.做5-7ul血清直接qPCR 3 replicates

2.做5-7ul血清裂解直接qPCR 3 replicates

3.根据1.2.选择做5-7ul血清直接/裂解smart建库 3 replicates

4.根据3.选择5-7ul或更多血清smart建库

5.裂解血清+Tn5建库（SHERRY）【第一次在血清（液体）中，不提取RNA，直接使用Tn5建库】

6.分4种组分，分别裂解后，直接进行smart或SHERRY建库，分析不同组分RNA成分

方案三：异想天开，省略建库流程，直接测序（如果无法实现，可直接采用三代测序检测血样）

直接设计针对转录组探针（beads with barcode (钓竿)+random probe (钓饵) +Tn5 (网兜)）

关键在于微量裂解液中的杂质问题、probes pool设计以及Tn5利用（一种直接无差别切，切成200bp的小段，另一种特异切，只切probe序列前后）

（1）直接在无粘稠物稀裂解液中加入磁性beads，孵育，洗涤并在beads上反转扩增，Tn5/cas9将序列切下，建库完成

（2）直接在血液中加入磁性beads，孵育，洗涤，Tn5/cas9将序列切下，直接完成

（3）直接向flowcell中加Tn5 tagmentated RNA，测序



### 2019 Small Input Liquid Volume Extracellular RNA Sequencing (SILVER-seq)

In liquid biopsy

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription, secondstrand complementary DNA (cDNA) synthesis, adapter ligation, and PCR amplification

+ ​	**[Pipeline](https://genemo.com/technology/silver-seq)**

<img src="C:\Users\Tao\Desktop\tech\SILVER-seq pipeline.png" alt="SILVER-seq pipeline" style="zoom:40%;" />

> Construction of SILVER-seq Sequencing Libraries. The starting volume of each serum sample was between 3 uL and 7 uL. Any serum sample of volume smaller than 7 uL was supplemented with Ultrapure water to reach a total volume of 7 uL. EVs were lysed, and RNPs were disassociated
> by mixing the sample with 1.7 uL of 11.5 mM DTT solution, 0.5 uL of 40 U/uL RNase inhibitor, and 2.8 uL of lysis buffer consisting of 10 mM Tris-HCl, 0.2% w/v SDS solution, and 4% w/v Nonidet P-40. First- and second-strand cDNA syntheses were carried out as follows. The resulting material from the previous step was incubated with a mix of random hexamer and oligo-dT primers at 70 ℃ for 2 min, and incubated with temperaturesensitive double-strand DNase (HL-dsDNase) at 37 ℃ for 10 min, then at 65 ℃ for 5 min for enzyme deactivation, and subsequently incubated with reverse transcriptase at 25 ℃ for 5 min followed by 40 ℃ for 30 min and 70 ℃ for 10 min. The resulting material was incubated with DNA polymerase and template-switching oligo at 25 ℃ for 15 min, at 37 ℃ for 15 min, and then 70 ℃ for 10 min and subjected to end repair, adaptor ligation, size selection, amplification, and rRNA sequence depletion. The product library was quantified with Qubit (Invitrogen), and measured by Bioanalyzer (Agilent) for size distribution.

+ **Advantages and discovery**

1. extreme low input
2. small variablility
3. detect tissue specific genes
4. distinguish sex by reads mapping to sex chromosomes
5. Similarity of Global exRNA but Differentially Expressed exRNAs, more up- than down-regulated exRNA in cancer
6. <u>*The Differentiating Power of miRNAs and Mt tRNAs to Classify Breast Cancer Patients and Normal Donors*</u>

+ **Questions generated**

> the pipeline illustrated they use TSO, but still add adaptor by ligation.

1. Why?

> Article said KRAS gene show up in seq data, but mostly derived from the 4th exon. And it is a common phenomenon,  78.1% of the samples detected 4th exon.

2. Can we conclude more tissue genes like KRAS, and explain the pattern. Why a specific RNA fragment show up in serum? does this fragment shall a common pattern?

> We tested sex, ethnicity, body mass index, smoking status, and drinking status as potential confounders. None of these factors exhibited any noticeable impact to the correlation between
> exRNA age and chronological age (all adjusted P values > 0.9). <u>*Taken together, exRNA age is predictive of chronological age.*</u>

3. <u>*cancer prediction by liquid biopsy! Conclude a development road of phase&gene expression. (by utilize single cell pseudo time analysis) Aims to prediction cancer before any pathological change！*</u>

> We suspect that the biological variation in exRNA content between 2 serum droplets is primarily attributable to the different composition of exRNA carriers. These carriers include extracellular vesicles (EVs), RNPs, lipoprotein complexes (22), nonmembranous nanoparticles (exomeres) (26), and other tobe-identified types. <u>*It would require future technology developments to quantify the variability of cargo composition between 2 serum samples, especially between 2 small-volume samples.*</u>

3. isolated different cargo and sequencing respectively, using the data to conclude different RNA expression in different cargos.

+ tips

  Different kits/reagents RNA extraction results

<img src="C:\Users\Tao\Desktop\tech\SILVER-seq RNA extraction.png" alt="RNA kits/reagents" style="zoom:67%;" />

### 2019 Sequencing HEteRo RNA-DNA-hYbrid (SHERRY)(full length)

In single cell

~~RNA extraction~~, ~~ribosomal RNA depletion?~~, reverse transcription, secondstrand complementary DNA (cDNA) synthesis, ~~adapter ligation~~, and PCR amplification + RNA/cDNA hybrid Tagmentation

+ **Pipeline**

<img src="C:\Users\Tao\Desktop\tech\SHERRY.png" alt="SHERRY" style="zoom:50%;" />

> **Tn5 Transposome Tagmentation.** As for RNA/DNA hybrid, tagmentation was performed in buffer containing 10 mM Tris-Cl (pH 7.6), 5 mM MgCl2, 10% N,N-Dimethylformamide, 9% PEG8000 (VWR Life Science, Cat. No. 97061), 0.85 mM adenosine 5´-triphosphate (ATP; NEB, Cat. No. P0756). In SHERRY
> library preparation, we used 0.05, 0.006, and 0.003 μL Tn5 transposome for input of 200 ng, 10 ng, and 100 pg total RNA, respectively. scSHERRY also used 0.003 μL Tn5 transposome. The transposome could be diluted in 1× Tn5 dialysis buffer [50 mM Hepes (pH 7.2, Leagene, Cat. No. CC064), 0.1 M NaCl (Invitrogen, Cat. No. AM9759), 0.1 mM ethylenediaminetetraacetic acid (Invitrogen, Cat. No. AM9260G), 1 mM dithiothreitol, 0.1% Triton X-100, 10% glycerol]. The reaction was
> incubated at 55 °C for 30 min.
> **SHERRY Library Preparation and Sequencing. **As for purified 10 or 200 ng total RNA input, the tagmentation product was firstly gap-filled with 100 units of SuperScript II and 1 × Q5 High-Fidelity Master Mix at 42 °C for 15 min, then SuperScript II was inactivated at 70 °C for 15 min. When inputting 100 pg total RNA, the extension enzyme was replaced with 4 units of Bst 2.0 WarmStart DNA Polymerase (NEB, Cat. No. M0538). Correspondingly, the reaction temperature was up-regulated to 72 °C and inactivation was performed at 80 °C for 20 min. After that, indexed common primers were added to perform PCR. We performed 12, 15, and 25 cycles of PCR for input of 200 ng, 10 ng, and 100 pg total RNA, respectively. The resulting library was purified with 1:1 ratio by VAHTS DNA Clean
> Beads. Quantification was done by Qubit 2.0 and quality check was done by Fragment Analyzer Automated CE System. The sequencing platform we used was Illumina NextSEq 500 or HiSEq 4000.

+ **Advantages and discovery**

1. proved Tn5 can bind to DNA/RNA hybrids and tagmentation activity of our in-house pTXB1 Tn5 was 10-fold higher than V50 and 500-fold higher than ATM. (pTXB1 Tn5 is uesd in LANTI)
2. a dynamic range 10pg-10ug
3. fast (4h) and easy(head on time 30min) and cheap
4. compared with Smart-seq2, comparable quality and lower GC bias.
5. all in one tube,  promising for high-throughput application

+ **Questions generated**

1. PCR bias? Exists, PCR 15 cycles to solve. Full length transcript result in unevenness in 5' and 3' (3' bias).

> <u>In an attempt to solve this problem, we added template-switching oligo primer, the sequence and concentration of which was the same as Smart-seq2 protocol</u>, to the reverse transcription buffer to mimic the Smart-seq2 reverse transcription conditions. The resulting hybrid was then tagmented and amplified following standard SHERRY workflow. <u>This produced much improved evenness across transcripts, although some of the sequencing parameters dropped accordingly.</u> 

2. rRNA depletion? Not mention.

+ tips

  Tn5 also binds to DNA/RNA hybrids

  > These structural similarities among Tn5, RNase H, and MMLV reverse transcriptase and the docking results further supported the possibility that Tn5 can catalyze the strand transfer reaction on RNA/DNA heteroduplex

### 2017 Linear Amplification via Transposon Insertion (LIANTI，WGA）

+ **Pipeline**

<img src="C:\Users\Tao\Desktop\tech\LANTI pipeline.png" alt="LANTI" style="zoom:80%;" />

+ **Advantages and discovery**

1. reduced amplification bias and errors
2. low CV values with respect to all bin sizes, offering high accuracy for CNV detection
3. amplification noise by digital counting of the inferred fragment numbers
4. improves the resolution of micro-CNV detection to ~10 kb (uesd to be 100kb CNV)
5. C-T, A-G, G-T false positive SNV generated from spontaneous mutation of DNA bases

+ **Questions generated**

1. C-to-T false-positive predominance? Solved by treated with uracil–DNA glycosylase.
2. can't distinguish and sequence the amplicons from both strands of the duplex DNA simultaneously, kindred cells have to be used to correct SNV false positives generated due to chemical stability of DNA bases.

### 2012 Multiple annealing and looping-based amplification cycles（MALBAC）

+ **Pipeline**

<img src="C:\Users\Tao\Desktop\tech\MALBAC pipeline.png" alt="MALBAC" style="zoom:50%;" />

+ **Advantages and discovery**

1. no false positives

> By sequencing three kindred cells, we were able to identify individual single-nucleotide variations (SNVs), with no false positives detected.

2. Transitions are not more common than transversion

> Both significantly low tstv ratios indicate that transitions are not favored over transversion for newly acquired SNVs in this cancer cell line.

### 2014 Smart seq2(full length)

+ **Pipeline**

  <img src="C:\Users\Tao\Desktop\tech\Smartseq2 pipeline.png" alt="smartseq2" style="zoom:60%;" />

### 2017 NEBnext(short fragment)

+ **Pipeline**

![NEBnext](C:\Users\Tao\Desktop\tech\NEBnext pipeline.png)



​                                                                                                                                            [more readings about WGA](http://www.ebiotrade.com/custom/genome/160601/index.htm)

# RNA seq tech in one table

| Name       | Year | Input        | Coverage | Number     | Adaptor     | Length      | Variability  |
| ---------- | ---- | ------------ | -------- | ---------- | ----------- | ----------- | ------------ |
| SILVER-seq | 2019 | 5-7ul/ 10pg  | 80%      | ~30k TPM>5 | 132bp(+TSO) | 200-300bp   | Small        |
| SHERRY     | 2019 | 10pg-20ng    | 50%-90%  | 8k-10k     | 136bp       | ~100bp      | robustness   |
| Smart-seq2 | 2014 | 250 pg–10 ng | -        | ~10k       | 30+100?     | -           | -            |
| LANTI      | 2017 | ~6pg         | 97% 30x  | -          | 19+121?     | ~400bp      | -            |
| MALBAC     | 2012 | ~6pg         | 93% 25x  | -          | 62+?        | 500- 1500bp | reproducible |
| NEBNext    | 2017 | 10ng-1ug     | -        | -          | 121bp       | -           | -            |

# Plasma Component Isolation Strategy

### Components

![components](C:\Users\Tao\Desktop\tech\components.png)

### Different RNA species in different cargo

<img src="C:\Users\Tao\Desktop\tech\species in different cargo.png" alt="RNA species in cargo short" style="zoom:50%;" />

<img src="C:\Users\Tao\Desktop\tech\types in different cargo.png" alt="types in different cargo long" style="zoom:40%;" />

1. differ in cell species but need to confirm in plasma
2. mostly miRNA but abundant in NV

> Many of the most abundant miRNAs were more associated with extracellular NV fractions

3. VTRNA & tRNA & YRNA in NV(non-vesicular)

> YRNAs and vault RNAs (VTRNA) were enriched in extracellular samples with VTRNA in particular associated with NV fractions.

4. not very much rRNA in short RNA?

> Distinct ribosomal RNA (rRNA) peaks (18S and 28S) were diminished in the extracellular lEV, sEV, and NV samples, while small RNA species were enriched.
>
> Short RNA libraries were prepared using NEBNext Small RNA Library Prep Set for Illumina (New England BioLabs, Ipswich, MA, USA). **this plot is short RNA seq**
>
> For long RNA library preparation, a Ribo-zero Magnetic Gold rRNA removal kit (Epicenter, IIlumina) was used to remove ribosomal RNA from the total RNA.

### Secretion model

![secretion model](C:\Users\Tao\Desktop\tech\secretion model.png)

### Pipeline

+ summary

![pipeline summary](C:\Users\Tao\Desktop\tech\isolation strategy pipeline summary.png)

+ Product

1. centrifugation ——> Debris IEVs
2. High-resolution density gradient ——> Non-vesicular fractions(Histone)

3. Direct Immunoaffinity capture(CD63) ——> classical exosomes(CD9/CD63/CD81)

4. Non-exosomal sEVs(Annexin A1/2)

+ High-resolution density gradient pipeline

<img src="C:\Users\Tao\Desktop\tech\high-resolution gradient centrifuge pipeline.png" alt="High-resolution density gradient" style="zoom:50%;" />

+ DIC pipeline

<img src="C:\Users\Tao\Desktop\tech\DIC pipeline.png" alt="DIC pipeline" style="zoom:50%;" />

+ Detailed methods

1. Blood EVs crude extraction 

> Blood was drawn into BD Vacutainer Blood Collection Tubes (BD Bioscience) containing either Acid Citrate Dextrose Solution A or Buffered Sodium Citrate as anticoagulants. The first tube drawn was discarded. Further processing of samples was initiated within 20 min of blood draw. Plasma was generated by first centrifugation of the blood at 3000 3 g for 15 min and then a second round of centrifugation of the supernatant at 30003g for 15 min tube to ensure that no platelets remained (see also Figure S3D). The resulting plasma samples were immediately diluted ~1:20 in ice cold PBS and spun at 15,000 x g for 40 min to pellet and remove lEVs and microparticles. The supernatant was filtered through a 0.22 mm pore PES filter (Millipore). Clarified supernatants were subjected to ultracentrifugation at 120,000 3 g for 4 h in a SW 32 Ti Swinging Bucket rotor to sediment sEVs. Pellets of crude sEVs (P120) were resuspended in ice-cold PBS, tubes were filled with PBS, and then subjected to ultracentrifugation at 120,000 3 g for 4 h. The washed pellet was resuspended again and subjected to a second wash step, again at 120,000 3 g for 4 h. The washed pellet was resuspended in ice-cold PBS. Crude plasma sEV samples were further purified by high-resolution iodixanol density gradients fractionation (see below and Figure S3D). At no time during the process were plasma or plasma sEVs subjected to temperatures below 4℃.

2. High-resolution (12%–36%) iodixanol density gradient fractionation

> Iodixanol (OptiPrep) density media (Sigma-Aldrich, St Louis, MO, USA) were prepared in ice-cold PBS immediately before use to generate discontinuous step (12%–36%) gradients. Crude pellets of sEVs (P120) were resuspended in ice-cold PBS and mixed with ice-cold iodixanol/PBS for a final 36% iodixanol solution. The suspension was added to the bottom of a centrifugation tube and solutions of descending concentrations of iodixanol in PBS were carefully layered on top yielding the complete gradient. Identical gradients without sample were generated in the same manner for later determination of fraction densities (Figure S1A). The bottom-loaded 12%–36% gradients were subjected to ultracentrifugation at 120,0003 g for 15 h at 4℃ using a SW41 TI Swinging Bucket rotor (k factor of 124, Beckman Coulter). Twelve individual fractions of 1 mL were collected from the top of the gradient. From the duplicate gradient, fraction densities were measured using a refractometer (ATAGO, Tokyo, Japan). For Nanoparticle Tracking Analysis (NTA), fractions were pooled and diluted in particle-free PBS. For immunoblotting, each individual 1 mL fraction was transferred to new ultracentrifugation tubes, diluted 12-fold in PBS and subjected to ultracentrifugation at 120,000 3 g for 4 h at 4℃ using a SW41 TI swinging bucket rotor. The resulting pellets were lysed in cell lysis buffer (see below) for 30 min on ice. For RNA and DNA extraction, fractions were pooled, transferred to new ultracentrifugation tubes, diluted approximately 6-fold in PBS and subjected to ultracentrifugation at 120,000 3 g for 4 h at 4℃ using a SW 32 Ti Swinging Bucket rotor.

3. 6%–30% iodixanol density gradient fractionation

> Crude pellets of sEVs (P120) were resuspended in ice-cold PBS and mixed with ice-cold iodixanol/PBS for a final 30% iodixanol solution. The suspension was added to the bottom of a centrifugation tube and solutions of descending concentration of iodixanol in PBS were carefully layered on top yielding the complete gradient. Identical gradients without sample were generated in the same manner for later determination of fraction densities (Figure S5A). The bottom-loaded 6%–30% gradients were subjected to ultracentrifugation at 120,000 3 g for 15 h at 4℃ using a SW41 TI Swinging Bucket rotor. Ten individual fractions of 1mL were collected from the top of the gradient.

4. RNA extraction from cells, large EVs and small EVs, and RNA analysis

> RNA was extracted using miRCURY RNA Isolation Cell and Plant Kit (Exiqon, 300110) according to the manufacturer’s protocol with elution in a volume of 50 ml. RNA was quantified and 260/280 ratio assessed using a NanoDrop 2000 (Thermo Scientific), and Qubit 2.0 Fluorometer (Invitrogen, Carlsbad, California, CA, USA). Profiles of RNA species present in samples were generated using Agilent RNA Nano 6000 and Agilent RNA Pico 6000 kits on a 2100 Bioanalyzer instrument (Agilent Technologies).

5. Direct Immunoaffinity Capture (DIC) of exosomes

> Immediately after collection, cell-conditioned medium was subjected to differential centrifugation at 400 x g, 2,000 x g and 15,000 x g at 4℃. The supernatant was filtered through a 0.22 mmpore PES filter (Millipore) to generate pre-cleared medium. All following steps were also performed at 4℃. Pre-cleared medium was split three ways, one portion were incubated with magnetic beads directly conjugated to anti-mouse antibodies directed at CD63, CD81 or CD9 (ThermoFisher Scientific), one portion incubated with magnetic beads conjugated to mouse IgG, and incubation was allowed to proceed with nutation and rotation for 16 h (Figure 4A). The third portion was subjected to ultracentrifugation and washing to generate a crude sEV pellet as described above (P120). After incubation, the beads were washed four times in ice-cold 0.1% BSA-PBS (pH 7.4, filtered through a 0.22 mmmembrane), and finally, washed one time in PBS pH 7.4 (pH 7.4, filtered through a 0.22 mm membrane). Immediately following the last wash, the exosome-loaded beads were resuspended first in cell lysis buffer and LDS sample buffer for 30 min on ice, and then resuspended in LDS sample buffer followed by heating to 70℃ for 10 min to release proteins. The beads were removed from the suspension by using a magnet and the clarified lysate used for immunoblot analysis. In some cases, immediately following the last wash step, the exosome-loaded beads were lysed for DNA extraction (Figure S6E and see below). DIC of exosomes directly from human plasma was performed as described above except that the supernatant in these cases was raw, undiluted and unfiltered, plasma (generated by two rounds of 3000 x g centrifugation for 15 min).