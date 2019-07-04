# Index Hopping Analysis

__[Characterization and remediation of sample index swaps by non-redundant dual indexing on massively parallel sequencing platforms](https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-018-4703-0)__

_Costello et al._ - [10.1186/s12864-018-4703-0](https://doi.org/10.1186/s12864-018-4703-0)


* HiSeq X, 3000/4000 utilize a patterned flowcell.
* The patterned flowcell has been observed to cause higher levels of index swapping. The patterned flowcell ustilizes ExAmp chemistry to provide higher yields, but this also contributes to greater levels of swapping because adapters/primers are not washed away as they are on HiSeq 2500.

![Single v. Dual indexing](img/index_swap.png)

<small>Single indexing was obsered to cause greater levels of contamination</small>

PCR-plus - 8 Extra cycles

### Factors contributing to swapping

- Presence of excess free primer or adapters
- Increases as plex increases. Prob(self-swaps) decreases, and prob of swaps with other samples increases.
- Library prep method influences swap rates with DNA shearing + adapter ligation + HiSeq - Highest rates
- Higher rates observed for chimeric reads.
- Higher rates at lower % GC, b/c shorter fragments with lower %GC amplify more efficiently with polymerase based amplification assays - which is what the ExAmp chemistry ustilizes.
- Swapping also occurs during exome capture

![](img/table.png)

- "Index switching causes spreading of signal" paper reported 10% swap rate.
- Highest found in this paper is 6%.
- Typical swap rates:
  - 3% - PCR- (free)
  - 0.25% - PCR+ genomes.
- Authors hypothesize higher swap rates in PCR-free libraries due to low library fragment yield. This is likely due to the dilution step.
- PCR-plus libraries are diluted following PCR, reducing the ratio of adapter to library fragments.
- They hypothesize that the dilution of PCR-plus libraries reduces the ratio of free adapter to library fragments.
- Index swapping examined at the flowcell - lane level.
- Observed rates of 0.2 - 6%, avg. 1%
- In the case of WES, most adapters would be lost during the exome capture stage, and PCR further reduces likelihood of swapping.
- Swapping is therefore more of an issue with WGS without adequite cleanup.

![](img/by_lane.png)

<small>Swap rates are examined on a per-lane per-flowcell basis</small>

![](img/swapped_chimeras.png)

<small>Both smaller inserts and chimeras have increased swap rates</small>


__[A novel post hoc method for detecting index switching finds no evidence for increased switching on the Illumina HiSeq X](https://onlinelibrary.wiley.com/doi/full/10.1111/1755-0998.12713)__

_Owens et al._

Examines unbalanced heterozygoes which would be produced by index switching.

* Working with WGS sunflower (_Helianthus annuus).
* 350 bp size.
* Prob. is that only a single read is observed to switches in their dataset. 
* Calculated the bionomial probability that the rare allele would be found in one or more samples based on the allele frequency for all samples sequenced with that machine.

$\hat{p} = 1 - (1-f)^{2n}$

If index switching is occuring, then $\hat{p} > p$.

![](img/phat.png)