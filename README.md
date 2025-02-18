# ChIP-Seq Analysis
## Understanding the gene regulatory mechanisms by RUNX1

In this analysis, we see the role of RUNX1, by building upon the study by Barutcu et al. (2016), where they employed a multi-omics approach, including RNA-seq, ChIP-seq, and Hi-C analyses, to find the regulatory landscape governed by RUNX1 in breast cancer. The aim is to find the genome-wide binding sites of RUNX1 within the MCF7 genome.

## Methods
Raw sequencing data were organized using a sample sheet `sample_sheet.csv` and retrieved via the `wget_files` rule. Subsequent quality control involved FastQC (v.0.12.1) for assessing read quality, followed by adapter trimming using Trimmomatic (v0.39). Alignment to the GRCh38 reference genome was achieved with Bowtie2 (v2.5.3), while SAMtools (v1.20) facilitated sorting and indexing of resultant BAM files. Quality metrics were obtained using SAMtools flagstat, and a comprehensive report was generated via MultiQC (v1.21). Read coverage across the genome was computed using deepTools' bamCoverage (v3.5.4), with Pearson correlation coefficients visualized using plotCorrelation. Peak calling was executed using HOMER (v4.11), with BEDTools (v2.31.0) employed for peak intersection analysis. Peaks were subsequently annotated using HOMER's `annotatePeaks.pl` script with a GTF file, and motif enrichment analysis was performed using HOMER's `findMotifsGenome.pl`. Visualization of read coverage around peak regions was accomplished with plotProfile. 

`chip_seq.snake` → full snakemake workflow

## References
1. Barutcu, A. R., Hong, D., Lajoie, B. R., McCord, R. P., van Wijnen, A. J., Lian, J. B., Stein, J. L., Dekker, J., Imbalzano, A. N., & Stein, G. S. (2016). RUNX1 contributes to higher-order chromatin organization and gene regulation in breast cancer cells. Biochimica et biophysica acta, 1859(11), 1389–1397. https://doi.org/10.1016/j.bbagrm.2016.08.003
2. Andrews, S. (2010). FastQC: A Quality Control Tool for High Throughput Sequence Data [Online]. Available online at: http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
3. Bolger, A. M., Lohse, M., & Usadel, B. (2014). Trimmomatic: a flexible trimmer for Illumina sequence data. Bioinformatics (Oxford, England), 30(15), 2114–2120. https://doi.org/10.1093/bioinformatics/btu170
4. Philip Ewels, Måns Magnusson, Sverker Lundin, Max Käller, MultiQC: summarize analysis results for multiple tools and samples in a single report, Bioinformatics, Volume 32, Issue 19, October 2016, Pages 3047–3048, https://doi.org/10.1093/bioinformatics/btw354
5. Heinz S, Benner C, Spann N, Bertolino E et al. Simple Combinations of Lineage-Determining Transcription Factors Prime cis-Regulatory Elements Required for Macrophage and B Cell Identities. Mol Cell 2010 May 28;38(4):576-589. PMID: 20513432
6. Aaron R. Quinlan, Ira M. Hall, BEDTools: a flexible suite of utilities for comparing genomic features, Bioinformatics, Volume 26, Issue 6, March 2010, Pages 841–842, https://doi.org/10.1093/bioinformatics/btq033
7. Petr Danecek, James K Bonfield, Jennifer Liddle, John Marshall, Valeriu Ohan, Martin O Pollard, Andrew Whitwham, Thomas Keane, Shane A McCarthy, Robert M Davies, Heng Li, Twelve years of SAMtools and BCFtools, GigaScience, Volume 10, Issue 2, February 2021, giab008, https://doi.org/10.1093/gigascience/giab008
8. Ramírez, F., Dündar, F., Diehl, S., Grüning, B. A., & Manke, T. (2014). deepTools: a flexible platform for exploring deep-sequencing data. Nucleic acids research, 42(Web Server issue), W187–W191. https://doi.org/10.1093/nar/gku365
9. Mölder, F., Jablonski, K.P., Letcher, B., Hall, M.B., Tomkins-Tinch, C.H., Sochat, V., Forster, J., Lee, S., Twardziok, S.O., Kanitz, A., Wilm, A., Holtgrewe, M., Rahmann, S., Nahnsen, S., Köster, J., 2021. Sustainable data analysis with Snakemake. F1000Res 10, 33.
