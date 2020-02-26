# Tn5

Tn=transposon, Tnp=transposase, IS=insertion sequence, ES=end sequence

[一个非常有意思的文档](https://wenku.baidu.com/view/1b607019302b3169a45177232f60ddccda38e6ac.html)

### History

###### (Reznikoff ,2008)Transposon Tn5

+ Tn5 was initially discovered as a side product of studies on R factor–encoded kanamycin resistance

  > In the course of these studies, it was discovered that the gene encoding kanamycin resistance could be transferred from the R factor to the bacteriophage λ genome by means of a process called transposition.
  >
  > Analysis of the transferred DNA structure revealed that it was composed of two inverted, almost identical sequences called **IS50L and IS50R** that bracket three genes encoding antibiotic resistances: kanamycin resistance, bleomycin resistance, and streptomycin resistance


### 00. Mechanism——cut and paste

###### (Reznikoff ,2008)Transposon Tn5

precisely excised from its original location in the donor DNA and then is inserted into a target sequence

+ Tool——Tnp (IS50R), no host proteins are required for Tnp’s action

  <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5.png" alt="Tn5 sequence" style="zoom:70%;" />

  + All of the steps in transposition are catalyzed by a 476-residue transposase protein (Tnp) encoded by IS50R (IS50L encodes an inactive truncated version of Tn5).

  + point mutation lead to hyperactive form Tnp,  Mosaic ES are also contribute to hyperactive version of Tnp
  + Tnp must interact in a sequence specific fashion with inverted 19-bp DNA sequences (end sequences or ESs) at the termini of IS50 in order to catalyze transposition but the interaction with target DNA has only modest specificity.

+ molecular function

  1. **Randomly! Tnp identify and bind to the ES sequences**

     - [ ] bind and slide
     - [ ] hopping/jumping
     - [x] direct transfer

     much like a monkey traveling through the jungle
     
2. **forms a binary synaptic complex composed of two ES-bound Tnps** (scaffold for catalytic, but Tnp:Tnp dimeric complex formation occurs prior to Tnp ES binding)对应蛋白质N端的是基因序列的5端
  
3. **Tnp cleave DNA and releases the ES sequence**
  
   ①Attack of activated H2O: a water-mediated nicking of one strand (transferred strand), generating a 3'-OH group
  
   ②Hairpin formation: a strand transfer reaction in which the 3'-OH group attacks the opposite strand to generate a hairpin structure
  
   ③Resolution of hairpin: Tnp catalyzes cleavage of the hairpin DNA structure using water as the nucleophile.
  
4. **Dimeric Tnp-ES DNA complex then binds to target DNA to form a target capture complex**
  
5. **Tnp catalyzes insertion of the ES DNA**(插入是由synaptic complex Tnp所抓住的平末端3’-OH完成的，randomly)
  
   nucleophylic attacks by both 3'-OH groups on either side of a 9-bp target DNA sequence
  
   <u>* And what is the 9-bp target DNA sequence requirement? how to design?</u>
  
   <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5 9bp target.png" alt="Tn5 9-bp target" style="zoom:50%;" />
  
   > Thus thousands of inserts have been sequenced and from these data one can study the sequence biases involved in Tn5 insertion, meaning the sequence biases involved in target capture (60). From this analysis it has been determined that the preferred target sequence extends approximately 19 bp with a 9-bp core sequence (as predicted from the observed 9-bp duplication generated during integration) surrounded by∼5 bp on either side in which some preferences are demonstrated (see Figure 7). Thus the target for Tn5 is not completely random, although almost any sequence can be chosen at some frequency, and the randomness is sufficient for most biotechnological applications.
  
6. **Disassemble and repair the 9 base gaps on either edge of the insertion by host**

### 01. Application

###### (Picelli,2014)Tn5 transposase and tagmentation procedures for massively scaled sequencing projects

+ pTXB1-Tn5, the same in SHERRY (SHERRY also tried a D188E mutation Tn5)

> a hyperactive Tn5 allele harboring the classical E54K and L372Pmutations (but wild-type at M56) into pTBX1

+ preannealing of adaptor oligos on Tn5 (we can add UMI here)

> 1. Functional **mosaic-end (ME)** oligonucleotideswas separately annealed with equal amounts of **Adaptor A**  and Adaptor B . 
>
>    ME: 5’-CTGTCTCTTATACACATCT-3’, 100μM
>
>    Adaptor A: 5’-TCGTCGGCAGCGTCAGATGTGTATAAGAGACAG-3’, 100μM
>
>    Adaptor B: 5’-GTCTCGTGGGCTCGGAGATGTGTATAAGAGACAG-3’, 100μM
>
>    <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\SHERRY ME_adaptor.png" alt="SHERRY ME+adaptor" style="zoom:50%;" />
>
> 2. The concentration of purified Tn5 was quantified by Qubit Protein Assay Kit (Invitrogen, Cat.No.Q33212) and took around **100μg** for transposome assembly. 
>
> 3. We mixed the Tn5 transposase with annealed ME-Adaptor A **or** B (20μM) in 45% glycerol (Sigma, Cat.No.G5516) thoroughly and incubated the mixture at 30°C for one hour. 
>
> 4. These two resulting transposomes (assembled with ME-Adaptor A/B) were then mixed together, ready for tagmentation or stored at -20°C.
>
> 5. As for RNA/DNA hybrid, tagmentation was performed in buffer containing 10mM Tris-Cl (pH 7.6), 5mM MgCl2, 10% N,N-Dimethylformamide, 9% PEG8000 (VWR Life Science, Cat.No.97061), 0.85mM ATP (NEB, Cat.No.P0756).
>
> 6. The reaction was incubated at 55°C for 30min.
>
>    <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\SHERRY Tn5 dose.png" alt="SHERRY Tn5 dose" style="zoom:50%;" />

> We observed that oligonucleotides containing the hyperactive ME sequences could be annealed to Tn5 already on the columns (so that excess unannealed oligonucleotides were discarded through the column)

+ magnesium chloride

  + too high affect PCR

    > The magnesium chloride concentration in the TAPS buffer (5 mM final concentration) was important, as higher concentrations gave progressively lower yields after enrichment PCR. 

  + too low

    > However, we failed to generate libraries when replacing magnesium for manganese
    > (in the form of MnCl2), indicating that magnesium is critical for tagmentation.

+ commercial reagents

  + tagmentation and enrichment PCR 

    **[Nextera kit (Illumina)](https://support.illumina.com/sequencing/sequencing_kits/nextera_xt_dna_kit/documentation.html)**

  + pico input

    + use PEG4000/6000/8000

      > while the data quality was comparable when using various PEG polymers, the average size of the libraries after enrichment PCR was inversely related to the polymer length, with the longest polymers giving the libraries with the shortest average size (Fig. 4C). This is an indirect confirmation that a more efficient tagmentation is obtained through a reduction of the available volume in which the transposase can operate.

    <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5 pico input.png" style="zoom:50%;" />

    + appropriate dose of Tn5(prevent overtagmentation)

      > Additionally, we observed that a larger percentage of reads became unmappable (e.g., adapter artifacts) in libraries made with in-house Tn5 from only 1 or 0.1 pg cDNA (Supplemental Fig. 5), likely the result of overtagmentation ofDNA due to highly excessive Tn5 amounts. To test this hypothesis, we generated additional libraries utilizing only a 1/100th of the Tn5 amount from 500, 1, and 0.1 pg of cDNA. Analyses of these libraries demonstrated much-improved mapping characteristics (Supplemental Fig. 4)

  + purification after tagmentation 

    DNA Clean & Concentrator-5 kit from Zymo Research

  + strip Tn5 off DNA

    SDS

    <img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5 SDS.png" alt="Tn5 SDS" style="zoom:70%;" />

  + performing the adaptor-ligated enrichment PCR (directly after srtipping)

    KAPA HiFiDNApolymerase


### 02. Attention

###### (Picelli,2014)Tn5 transposase and tagmentation procedures for massively scaled sequencing projects

+ fraction reads ∝ sequence length

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Tn5 read and length.png" alt="Tn5 read and length" style="zoom:70%;" />

Earlier work on Tn5 (Adey et al. 2010) observed that transposon-based libraries had a minimum insert length of 35 bp, but it has not been demonstrated whether shorter DNA fragments would be less efficiently captured in tagmentation derived sequencing libraries. We generated sequencing libraries based on Tn5 tagmentation of a DNA ladder of short fragments and **found that the fraction of reads aligning to fragments correlated (Spearman correlation = 0.8) with sequence length**. We concluded that tagmentation of fragments is fairly unbiased with respect to length, even down to 100-bp fragments.

### 03. Requirement

* transposon DNA (versions of which are commercially available)
* hyperactive Tnp (also commercially available)
* target DNA
* mixed in a suitable buffer containing Mg2+ and incubated to yield the transposition events.



### 04. Commercial kit

**[Nextera kit (Illumina)](https://support.illumina.com/sequencing/sequencing_kits/nextera_xt_dna_kit/documentation.html)**

基本情况：This guide explains how to prepare up to 384 dual-indexed paired-end libraries from DNA/Double-stranded cDNA/Single-cell RNA-Seq

特点：Uses tagmentation, an enzymatic reaction, to fragment DNA and add partial adapter sequences in only 5 minutes.

Input要求：

*Success depends on accurate quantification of input DNA！！

+ Requires only 1 ng input DNA.
+ Tagmentation cannot add an adapter directly to the distal end of a fragment, so a drop in sequencing
  coverage of ~50 bp from each distal end is expected. To ensure sufficient coverage of the amplicon target region, design primers to extend beyond the target region by 50 bp per end.
+ DNA with 260/280 absorbance ratio values of 1.8–2.0, which indicates a pure DNA sample
+ Target a 260/230 ratio of 2.0–2.2. Values outside this range indicate the presence of contaminants.
+ Assess DNA purity to ensure that the initial DNA sample does not contain > 1 mM EDTA and is free of organic contaminants, such as phenol and ethanol.

操作流程：

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Nextera workflow.png" alt="Nextare workflow" style="zoom:50%;" />

原理：

<img src="C:\Users\Tao\Documents\GitHub\Readings\tech\pictures\Nextera mechanism.png" alt="Nextera mechanism" style="zoom:50%;" />