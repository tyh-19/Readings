# RNA seq technology

### 2020 our new tech

###### 方案一：发展低bias、低成本、高通量的测序方法

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription+ UMI, secondstrand complementary DNA (cDNA) synthesis, adapter ligation, and PCR amplification 

（1）i-SMART validation

（2）一滴血浆(SILVER-seq, exRNA)+微流控(Drop-seq, single cell)+TSO(random primer + GGG + strapevidin, STRT-seq, MARS-seq, single cell)

高通量：一滴血浆，在微流控芯片上， 分成5-7ul液滴，与beads混合包裹，裂解，建库(Drop-seq)

低bias：一滴血浆，STRT-seq(use random primer(strapevidin) to reverse transcription)

###### 方案二：实现更快速、具有组分特异性的测序流程

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription, secondstrand complementary DNA (cDNA) synthesis, ~~adapter ligation~~, and PCR amplification

1.做5-7ul血清直接qPCR 3 replicates

2.做5-7ul血清裂解直接qPCR 3 replicates

3.根据1.2.选择做5-7ul血清直接/裂解smart建库 3 replicates

4.根据3.选择5-7ul或更多血清smart建库

5.裂解血清+Tn5建库（SHERRY）【第一次在血清（液体）中，不提取RNA，直接使用Tn5建库】

6.分4种组分，分别裂解后，直接进行smart或SHERRY建库，分析不同组分RNA成分

###### 方案三：异想天开，省略建库流程，直接测序（如果无法实现，可直接采用三代测序检测血样）,类似省略了核酸提取的TAC-seq，

直接设计针对转录组探针（beads with barcode (钓竿)+random probe (钓饵) +Tn5 (网兜)）

关键在于微量裂解液中的杂质问题、probes pool设计以及Tn5利用（一种直接无差别切，切成200bp的小段，另一种特异切，只切probe序列前后）

（1）直接在无粘稠物稀裂解液中加入磁性beads，孵育，洗涤并在beads上反转扩增，Tn5/cas9将序列切下，建库完成

（2）直接在血液中加入磁性beads，孵育，洗涤，Tn5/cas9将序列切下，直接完成

（3）直接向flowcell中加Tn5 tagmentated RNA/DNA hybrids，测序（只做第一链合成）

###### 方案四：滴血裂解，Tn5 tag+barcode，混合，+UMI建库

单次完成100+人血液建库，可以实现超高通量（大样本人群）或多维度（多处体液，配套多种细胞）

需要配套计算方法改进（分sample，分UMI）



### 2019 Small Input Liquid Volume Extracellular RNA Sequencing (SILVER-seq)

In liquid biopsy

~~RNA extraction~~, ribosomal RNA depletion, reverse transcription, secondstrand complementary DNA (cDNA) synthesis, adapter ligation, and PCR amplification

+ ​	**[Pipeline](https://genemo.com/technology/silver-seq)**

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\SILVER-seq pipeline.png" alt="SILVER-seq pipeline" style="zoom:40%;" />

> **Construction of SILVER-seq Sequencing Libraries** 
>
> 0. **Sample preparation**: The starting volume of each serum sample was between 3 uL and 7 uL. Any serum sample of volume smaller than 7 uL was supplemented with Ultrapure water to reach a total volume of 7 uL. 
> 1. **Lysis**: EVs were lysed, and RNPs were disassociated by mixing the sample with 1.7 uL of 11.5 mM DTT solution, 0.5 uL of 40 U/uL RNase inhibitor, and 2.8 uL of lysis buffer consisting of 10 mM Tris-HCl, 0.2% w/v SDS solution, and 4% w/v Nonidet P-40. 
> 2. **First- and second-strand cDNA syntheses**: The resulting material from the previous step was incubated with a mix of random hexamer and oligo-dT primers at 70 ℃ for 2 min, and incubated with temperaturesensitive double-strand DNase (HL-dsDNase) at 37 ℃ for 10 min, then at 65 ℃ for 5 min for enzyme deactivation, and subsequently incubated with reverse transcriptase at 25 ℃ for 5 min followed by 40 ℃ for 30 min and 70 ℃ for 10 min. The resulting material was incubated with DNA polymerase and template-switching oligo at 25 ℃ for 15 min, at 37 ℃ for 15 min, and then 70 ℃ for 10 min.
> 3. **Library construction**: subjected to end repair, adaptor ligation, size selection, amplification, and rRNA sequence depletion. The product library was quantified with Qubit (Invitrogen), and measured by Bioanalyzer (Agilent) for size distribution.

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

3. <u>*Cancer prediction by liquid biopsy! Conclude a development road of phase&gene expression. (by utilize single cell pseudo time analysis) Aims to prediction cancer before any pathological change！*</u>

> We suspect that the biological variation in exRNA content between 2 serum droplets is primarily attributable to the different composition of exRNA carriers. These carriers include extracellular vesicles (EVs), RNPs, lipoprotein complexes (22), nonmembranous nanoparticles (exomeres) (26), and other tobe-identified types. <u>*It would require future technology developments to quantify the variability of cargo composition between 2 serum samples, especially between 2 small-volume samples.*</u>

3. Isolated different cargo and sequencing respectively, using the data to conclude different RNA expression in different cargos.

+ tips

  Different kits/reagents RNA extraction results

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\SILVER-seq RNA extraction.png" alt="RNA kits/reagents" style="zoom:67%;" />

### 2019 Sequencing HEteRo RNA-DNA-hYbrid (SHERRY)(full length)

In single cell

RNA extraction, ~~ribosomal RNA depletion?~~, ~~reverse transcription~~, ~~secondstrand complementary DNA (cDNA) synthesis~~, ~~adapter ligation~~, and PCR amplification + RNA/cDNA hybrid Tagmentation

+ **Pipeline**

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\SHERRY.png" alt="SHERRY" style="zoom:50%;" />

> **Construction of SILVER-seq Sequencing Libraries**
> 
> 1. **Tn5 Transposome Tagmentation.** <u>As for RNA/DNA hybrid, tagmentation was performed in buffer containing 10 mM Tris-Cl (pH 7.6), 5 mM MgCl2, 10% N,N-Dimethylformamide, 9% PEG8000 (VWR Life Science, Cat. No. 97061), 0.85 mM adenosine 5´-triphosphate (ATP; NEB, Cat. No. P0756).</u> In SHERRY library preparation, we used 0.05, 0.006, and 0.003 μL Tn5 transposome for input of 200 ng, 10 ng, and 100 pg total RNA, respectively. scSHERRY also used 0.003 μL Tn5 transposome. The transposome could be diluted in 1× Tn5 dialysis buffer [50 mM Hepes (pH 7.2, Leagene, Cat. No. CC064), 0.1 M NaCl (Invitrogen, Cat. No. AM9759), 0.1 mM ethylenediaminetetraacetic acid (Invitrogen, Cat. No. AM9260G), 1 mM dithiothreitol, 0.1% Triton X-100, 10% glycerol]. <u>The reaction was incubated at 55 °C for 30 min.</u>
> 2. **SHERRY Library Preparation and Sequencing. **As for purified 10 or 200 ng total RNA input, the tagmentation product was firstly gap-filled with 100 units of SuperScript II and 1 × Q5 High-Fidelity Master Mix at 42 °C for 15 min, then SuperScript II was inactivated at 70 °C for 15 min. When inputting 100 pg total RNA, the extension enzyme was replaced with 4 units of Bst 2.0 WarmStart DNA Polymerase (NEB, Cat. No. M0538). Correspondingly, the reaction temperature was up-regulated to 72 °C and inactivation was performed at 80 °C for 20 min. After that, indexed common primers were added to perform PCR. We performed 12, 15, and 25 cycles of PCR for input of 200 ng, 10 ng, and 100 pg total RNA, respectively. The resulting library was purified with 1:1 ratio by VAHTS DNA Clean Beads. Quantification was done by Qubit 2.0 and quality check was done by Fragment Analyzer Automated CE System. The sequencing platform we used was Illumina NextSEq 500 or HiSEq 4000.

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

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\LANTI pipeline.png" alt="LANTI" style="zoom:80%;" />

+ **Advantages and discoveries**

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

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\MALBAC pipeline.png" alt="MALBAC" style="zoom:50%;" />

+ **Advantages and discoveries**

1. no false positives

> By sequencing three kindred cells, we were able to identify individual single-nucleotide variations (SNVs), with no false positives detected.

2. Transitions are not more common than transversion

> Both significantly low tstv ratios indicate that transitions are not favored over transversion for newly acquired SNVs in this cancer cell line.

[more readings about WGA](http://www.ebiotrade.com/custom/genome/160601/index.htm)

### 2014 Smart seq2(full length)

+ **Pipeline**

  <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Smartseq2 pipeline.png" alt="smartseq2" style="zoom:60%;" />
  
+ **Tip**

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5 tip.png" alt="Tn5" style="zoom:50%;" />

### 2012 Single-cell tagged reverse transcription sequencing (STRTseq)

+ **Pipeline**

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\STRTseq pipeline.png" alt="STRTseq pipeline" style="zoom:67%;" />

### 2019 Phospho-RNA-seq（full length）

+ **Pipeline**

  PNK treatment before library construction

+ **Advantages and discoveries**

1. modifiy mRNA/lncRNA 3'end and capture more mRNA/lncRNA

> Our results clearly showed that PNK treatment vastly increased the recovery of fragments
> either lacking a 5' P or having a 3' P. Lack of a 50 P and presence of a 30 P are both impediments to recovery of these fragments by standard small RNA-seq.

2. capture 14 bone fide microRNA that cannot be detect by traditional miRNA library kit

### 2018 TAC seq(proof-of-principle study)

+ **Pipeline**

<img src="C:\Users\Tao\Desktop\tech\TAC-seq pipeline.png" alt="TAC seq pipeline" style="zoom:50%;" />

+ **Advantages and discoveries**

> sensitivity, robustness and cost-efficiency

+ **Questions generated**

1. detect probe design/ low throughput?

> Combining high sensitivity and flexibility of NGS with cost-efficient and precise quantification of targeted methods

2. can we design RT random primer + UMI to conduct transcriptome sequencing 

+ **Tips**

1. UMI combination design

> UMI are valuable only if the number of UMI combinations is substantially larger than the sum of the target molecules in the studied sample. 

2. other ligation-PCR targeted sequencing

> MLPA (Schouten et al. 2002)
>
> MLPA-seq (Kondrashova et al. 2015)
>
> TempO-Seq (Yeakley et al. 2017) use splintR as RNA/DNA hybrid detector (like Tn5 in SHERRY)
>
> RASL-seq (Li et al. 2012) 
>
> DANSR (Sparks et al. 2012).

### 2017 NEBnext(short fragment)

+ **Pipeline**

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\NEBnext pipeline.png" alt="NEBnext" style="zoom:90%;" />



# RNA seq tech in one table

| Name       | Year | Input        | Coverage | Number     | Adaptor     | Length      | Variability  |
| ---------- | ---- | ------------ | -------- | ---------- | ----------- | ----------- | ------------ |
| SILVER-seq | 2019 | 5-7ul/ 10pg  | 80%      | ~30k TPM>5 | 132bp(+TSO) | 200-300bp   | Small        |
| SHERRY     | 2019 | 10pg-20ng    | 50%-90%  | 8k-10k     | 136bp       | ~100bp      | robustness   |
| Smart-seq2 | 2014 | 250 pg–10 ng | -        | ~10k       | 30+100?     | -           | -            |
| LANTI      | 2017 | ~6pg         | 97% 30x  | -          | 19+121?     | ~400bp      | -            |
| MALBAC     | 2012 | ~6pg         | 93% 25x  | -          | 62+?        | 500- 1500bp | reproducible |
| NEBNext    | 2017 | 10ng-1ug     | -        | -          | 121bp       | -           | -            |

# 2019 Plasma Components Isolation Strategy

DOI: 10.1016/j.cell.2019.02.029

### Components

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\components table.png" alt="components table" style="zoom:80%;" />

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\components.png" alt="components" style="zoom:90%;" />

### Different RNA species in different cargo

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\species in different cargo.png" alt="RNA species in cargo short" style="zoom:50%;" />

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
>
> Extracellular RNA (exRNA) was extracted from density gradientpurified sEV and NV pooled fractions. **Distinct ribosomal RNA (rRNA) peaks (18S and 28S) were diminished in the extracellular lEV, sEV, and NV samples, while small RNA species were enriched (Figure S2G).**

### Secretion model

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\secretion model.png" alt="secretion model" style="zoom:90%;" />

### Classical exosome

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\mass in classical exosome.png" style="zoom:80%;" />

### Pipeline

+ summary

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\isolation strategy pipeline summary.png" alt="pipeline summary" style="zoom:80%;" />

+ Product

1. centrifugation ——> Debris lEVs(Large extracelluar vesicular)
2. High-resolution density gradient ——> Non-vesicular fractions (Histone/RNP(tRNA/YRNA/vtRNA))

3. Direct Immunoaffinity capture(CD63) ——> classical exosomes (CD9/CD63/CD81)

4. Non-exosomal sEVs (Annexin A1/2)

+ High-resolution density gradient pipeline

  <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\high-resolution gradient centrifuge pipeline.png" alt="High-resolution density gradient" style="zoom:50%;" />

  + 根据fig. 1C, 低密度为sEV（exosome），高密度为NV
  + 且将低密度组分拿去离心，再次得到的高密度组分无细胞骨架产生，证明高速离心没有破坏exosome
  + 且低密度组分对穿膜试剂tritonX敏感
  + 电镜下也能看出低密度组分有杯型囊状结构，高密度组分则没有
  + 综上，证明高密度梯度离心能够分离exosome与NV

+ DIC pipeline
  
  + 这个方法并非是建立在已经密度梯度离心分离得到sEV的基础上，而可以在血浆或细胞外液中“直接”用抗体（“直接”连载beads上）将CD9/CD63/CD81 exosome，所以说这是一个not compromised method。结果是很多之前认为在exosome中的蛋白或RNA实际上都是混杂在exosome中的NP引入的，例如AGO1-4/GAPDH/PKM/VTRNA/tRNA等等

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\DIC pipeline.png" alt="DIC pipeline" style="zoom:50%;" />

+ Detailed methods

1. Blood EVs crude extraction 

> 0. Blood was drawn into BD Vacutainer Blood Collection Tubes (BD Bioscience) containing either Acid Citrate Dextrose Solution A or Buffered Sodium Citrate as anticoagulants. The first tube drawn was discarded. 
> 1. Further processing of samples was initiated within 20 min of blood draw. Plasma was generated by first centrifugation of the blood at 3000x g for 15 min and then a second round of centrifugation of the supernatant at 3000x g for 15 min tube to ensure that no platelets remained (see also Figure S3D). 
> 2. The resulting plasma samples were immediately diluted ~1:20 in ice cold PBS and spun at 15,000 x g for 40 min to pellet and remove lEVs and microparticles. The supernatant was filtered through a 0.22 mm pore PES filter (Millipore).**IEVs and debris are removed**
> 3.  Clarified supernatants were subjected to ultracentrifugation at 120,000 3 g for 4 h in a SW 32 Ti Swinging Bucket rotor to sediment sEVs. 
> 4. Pellets of crude sEVs (P120) were resuspended in ice-cold PBS, tubes were filled with PBS, and then subjected to ultracentrifugation at 120,000 3 g for 4 h. The washed pellet was resuspended again and subjected to a second wash step, again at 120,000 3 g for 4 h. The washed pellet was resuspended in ice-cold PBS. **Crude plasma sEV samples** were further purified by high-resolution iodixanol density gradients fractionation (see below and Figure S3D). At no time during the process were plasma or plasma sEVs subjected to temperatures below 4℃.

2. High-resolution (12%–36%) iodixanol density gradient fractionation

> 0. Iodixanol (OptiPrep) density media (Sigma-Aldrich, St Louis, MO, USA) were prepared in ice-cold PBS immediately before use to generate discontinuous step (12%–36%) gradients. 
>
> 1. Crude pellets of sEVs (P120) were resuspended in ice-cold PBS and mixed with ice-cold iodixanol/PBS for a final 36% iodixanol solution. 
> 2. The suspension was added to the bottom of a centrifugation tube and **solutions of descending concentrations of iodixanol in PBS were carefully layered on top yielding the complete gradient.** Identical gradients without sample were generated in the same manner for later determination of fraction densities (Figure S1A). An empty gradient (tube with iodixanol gradient but containing no sEV sample) was used run opposite an identical sample gradient, and density of fractions was measured by refractometry.
> 3. The bottom-loaded 12%–36% gradients were subjected to ultracentrifugation at 120,000x g for 15 h at 4℃ using a SW41 TI Swinging Bucket rotor (k factor of 124, Beckman Coulter).
> 4. Twelve individual fractions of 1 mL were collected from the top of the gradient. 
> 5. From the duplicate gradient, fraction densities were measured using a refractometer (ATAGO, Tokyo, Japan). 
> 6. * For Nanoparticle Tracking Analysis (NTA), fractions were pooled and diluted in particle-free PBS.
>    * For immunoblotting, each individual 1 mL fraction was transferred to new ultracentrifugation tubes, diluted 12-fold in PBS and subjected to ultracentrifugation at 120,000x g for 4 h at 4℃. The resulting pellets were lysed in cell lysis buffer (see below) for 30 min on ice. 
>    * For RNA and DNA extraction, fractions were pooled, transferred to new ultracentrifugation tubes, diluted approximately 6-fold in PBS and subjected to ultracentrifugation at 120,000x g for 4 h at 4℃.

3. 6%–30% iodixanol density gradient fractionation(for A1/2)

> Crude pellets of sEVs (P120) were resuspended in ice-cold PBS and mixed with ice-cold iodixanol/PBS for a final 30% iodixanol solution. The suspension was added to the bottom of a centrifugation tube and solutions of descending concentration of iodixanol in PBS were carefully layered on top yielding the complete gradient. Identical gradients without sample were generated in the same manner for later determination of fraction densities (Figure S5A). The bottom-loaded 6%–30% gradients were subjected to ultracentrifugation at 120,000 3 g for 15 h at 4℃ using a SW41 TI Swinging Bucket rotor. Ten individual fractions of 1mL were collected from the top of the gradient.

4. RNA extraction from cells, large EVs and small EVs, and RNA analysis

> RNA was extracted using miRCURY RNA Isolation Cell and Plant Kit (Exiqon, 300110) according to the manufacturer’s protocol with elution in a volume of 50 ml. RNA was quantified and 260/280 ratio assessed using a NanoDrop 2000 (Thermo Scientific), and Qubit 2.0 Fluorometer (Invitrogen, Carlsbad, California, CA, USA). Profiles of RNA species present in samples were generated using Agilent RNA Nano 6000 and Agilent RNA Pico 6000 kits on a 2100 Bioanalyzer instrument (Agilent Technologies).

5. Direct Immunoaffinity Capture (DIC) of exosomes

> 1. Immediately after collection, **cell-conditioned medium** was subjected to **differential centrifugation** at 400 x g, 2,000 x g and 15,000 x g at 4℃.
>
> 2. **The supernatant was filtered through a 0.22 mmpore PES filter (Millipore) to generate pre-cleared medium.**
>
>    *All following steps were also performed at 4℃.*
>
> 3. Pre-cleared medium was split three ways
>
>    + one portion were incubated with **magnetic beads directly conjugated to anti-mouse antibodies directed at CD63, CD81 or CD9 (ThermoFisher Scientific)**
>
>    + one portion incubated with magnetic beads conjugated to mouse IgG, and incubation was allowed to proceed with nutation and rotation for 16 h (Figure 4A). 
>
>    + **<u>[Former strategy: The third portion was subjected to ultracentrifugation and washing to generate a crude sEV pellet as described above (P120).]</u> **
>
> 4. After incubation, the beads were washed four times in ice-cold 0.1% BSA-PBS (pH 7.4, filtered through a 0.22 mmmembrane)
>
> 5. Finally, washed one time in PBS pH 7.4 (pH 7.4, filtered through a 0.22 mm membrane). 
>
> 6. Immediately following the last wash, the exosome-loaded beads were resuspended first in cell lysis buffer and LDS sample buffer for 30 min on ice
>
> 7. And then resuspended in LDS sample buffer followed by heating to 70℃ for 10 min to release proteins.
>
> 8. The beads were removed from the suspension by using a magnet and the clarified lysate used for immunoblot analysis. 
>
> 9. In some cases, immediately following the last wash step, the exosome-loaded beads were lysed for DNA extraction (Figure S6E and see below). 
>
>    *DIC of exosomes directly from human plasma was performed as described above except that **the supernatant in these cases was <u>raw, undiluted and unfiltered</u> plasma (generated by two rounds of 3000x g centrifugation for 15 min).**

# 2017 Plasma Components Isolation Strategy 

DOI: 10.1038/s41467-017-01196-x

+ fileration pipeline

![filteration pipeline](C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\filteration pipeline.png)

> 0. Fractionation and RNA isolation. **Approximately 100 ml** conditioned medium was used as input for exRNA isolation. 
> 1. Conditioned media was centrifuged at 300×g, 4 °C for 10 min, following by the additional centrifugation at 2000×g, 4 °C for 15 min, to remove cells and cell debris. 
> 2. To monitor EVs, the samples were diluted in DPBS and examined using the Nanoparticle Tracking Analysis system (NanoSight LM10; Malvern Instruments, UK), and EV concentrations were quantified within the optimal linear range (2–10 × 108 particles per 1 ml). 
> 3. For RNA preparation, 5 μl of SUPERase In RNase Inhibitor (Ambion) was added to the supernatants per 10 ml media. 
> 4. The media was then filtered sequentially through the 2 μm filter (GE Healthcare, UK), 0.8 μm filter (EMD Millipore, MA), and 0.22 μm filter (EMD Millipore), with no/minimal pressure applied. 
> 5. The filtrate was split to 15 ml per sample and further filtered through the 0.02 μm filter (GE Healthcare) with up to 75 psi pressure applied. To facilitate the 0.02 μm filtration, a mechanical syringe pump was designed and manufactured (Supplementary Fig. 2). 
> 6. Upon filtration, each filter was washed with 1ml DPBS (Corning), and the corresponding fractions were lysed with 600 μl lysis solution of the miRCURY RNA Isolation Kit—Cell & Plant (Exiqon, Denmark). The fractions collected on 0.02 μm filters were lysed with 900 μl lysis solution. The last flowthrough fractions of 0.02 μm filters were pooled together (up to 30 ml) and concentrated ~60 times using 3 kDa Amicon Ultra Centrifugal Filters (EMD Millipore) at 4000×g, 4 °C, for 60 min. The concentrates were collected and lysed with six volumes of the same lysis solution (Exiqon). 
> 7. Total RNA was then isolated from all fractions as recommended by miRCURY protocol, with on-column DNase treatment (Qiagen, Germany). The corresponding 1.2 ml of the source neurospheres were span down at 300×g, 4 °C for 5 min, and total cellular RNA was isolated from them and analyzed in parallel. The same protocol was carried out for RNA isolation from fresh media, with 500 ml media input. For RNA isolation from primary cells cultured in 24-well plates, the cells were lysed with 350 μl lysis solution per well. The concentrations of cellular and extracellular RNA were determined using the NanoDrop 2000 Spectrophotometer and Quant-iT RiboGreen RNA Assay Kit (Thermo Fisher Scientific), respectively. The RNA quality was examined using Agilent 2100 Bioanalyzer (Agilent, CA) and the RNA Integrity Number (RIN) estimated.