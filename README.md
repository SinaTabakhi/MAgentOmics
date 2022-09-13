# MAgentOmics: Multi-agent Feature Selection for Integrative Multi-omics Analysis

This repository implements the MAgentOmics proposed in the paper “Multi-agent Feature Selection for Integrative Multi-omics Analysis” [1]. It is the first attempt to apply a multi-agent system for multi-view feature selection to handle the high-dimensionality nature of multi-omics data. 

**Reference:**

[1] Sina Tabakhi and Haiping Lu, “[Multi-agent Feature Selection for Integrative Multi-omics Analysis](https://ieeexplore.ieee.org/document/9871758),” 2022 44th Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC), Glasgow, Scotland, United Kingdom, 2022, pp. 1638-1642, doi: [10.1109/EMBC48229.2022.9871758](https://doi.org/10.1109/EMBC48229.2022.9871758).

## Corrections

We have found one typo in the published paper. In Equation (1), we wrote the `min` operator instead of the `max` operator. Provided below is the correct format of the equation:

![This is an image](https://github.com/SinaTabakhi/MAgentOmics/blob/main/Equation_1.png)

It should be noted that we have correctly implemented the equation in the source code.

## Requirements

The code of the MAgentOmics method is implemented using `Python 3.10.2`. Below is the list of packages and frameworks we have used in the implementation:
* pandas 1.3.4
* numpy 1.20.3
* sklearn 0.24.2

## Multi-omics Data

Ovarian serous cystadenocarcinoma data from the TCGA were selected to conduct the paper experiments that can be downloaded from the [UCSC Xena Platform](https://xenabrowser.net/datapages/?cohort=TCGA%20Ovarian%20Cancer%20(OV)&removeHub=http%3A%2F%2F127.0.0.1%3A7222). Provided below are the characteristics of the Ovarian cancer multi-omics data.

|Omics Type	|Platform|Version|#Features|#Samples|Reference|
|------	|-----------------------|-----------------------|-------|------|------|
|DNA methylation|Illumina Infinium HumanMethylation27|2017-09-08|27,578|616|[Link](https://xenabrowser.net/datapages/?dataset=TCGA.OV.sampleMap%2FHumanMethylation27&host=https%3A%2F%2Ftcga.xenahubs.net&removeHub=http%3A%2F%2F127.0.0.1%3A7222&removeHub=https%3A%2F%2Fucscpublic.xenahubs.net&removeHub=https%3A%2F%2Fpancanatlas.xenahubs.net&removeHub=https%3A%2F%2Ficgc.xenahubs.net&removeHub=https%3A%2F%2Fpcawg.xenahubs.net&removeHub=https%3A%2F%2Ftoil.xenahubs.net&removeHub=https%3A%2F%2Fxena.treehouse.gi.ucsc.edu%3A443&removeHub=https%3A%2F%2Fgdc.xenahubs.net&removeHub=https%3A%2F%2Fatacseq.xenahubs.net&removeHub=https%3A%2F%2Fkidsfirst.xenahubs.net&removeHub=notebook%3A)|
|Gene-level copy number variation|Affymetrix SNP 6|2017-09-08|24,776|579|[Link](https://xenabrowser.net/datapages/?dataset=TCGA.OV.sampleMap%2FGistic2_CopyNumber_Gistic2_all_data_by_genes&host=https%3A%2F%2Ftcga.xenahubs.net&removeHub=http%3A%2F%2F127.0.0.1%3A7222&removeHub=https%3A%2F%2Fucscpublic.xenahubs.net&removeHub=https%3A%2F%2Fpancanatlas.xenahubs.net&removeHub=https%3A%2F%2Ficgc.xenahubs.net&removeHub=https%3A%2F%2Fpcawg.xenahubs.net&removeHub=https%3A%2F%2Ftoil.xenahubs.net&removeHub=https%3A%2F%2Fxena.treehouse.gi.ucsc.edu%3A443&removeHub=https%3A%2F%2Fgdc.xenahubs.net&removeHub=https%3A%2F%2Fatacseq.xenahubs.net&removeHub=https%3A%2F%2Fkidsfirst.xenahubs.net&removeHub=notebook%3A)|
|Gene expression RNA-seq|IlluminaHiSeq_RNASeqV2|2017-10-13|20,530|308|[Link](https://xenabrowser.net/datapages/?dataset=TCGA.OV.sampleMap%2FHiSeqV2_PANCAN&host=https%3A%2F%2Ftcga.xenahubs.net&removeHub=http%3A%2F%2F127.0.0.1%3A7222&removeHub=https%3A%2F%2Fucscpublic.xenahubs.net&removeHub=https%3A%2F%2Fpancanatlas.xenahubs.net&removeHub=https%3A%2F%2Ficgc.xenahubs.net&removeHub=https%3A%2F%2Fpcawg.xenahubs.net&removeHub=https%3A%2F%2Ftoil.xenahubs.net&removeHub=https%3A%2F%2Fxena.treehouse.gi.ucsc.edu%3A443&removeHub=https%3A%2F%2Fgdc.xenahubs.net&removeHub=https%3A%2F%2Fatacseq.xenahubs.net&removeHub=https%3A%2F%2Fkidsfirst.xenahubs.net&removeHub=notebook%3A)|

When the data have been downloaded, you should change the following lines of code in the Jupyter Notebook to read data from your directory:

```bash
omics1 = pd.read_csv('DataSet_OvarianCancer/DNA_methylation',sep='\t',index_col=0)
omics2 = pd.read_csv('DataSet_OvarianCancer/genelevel_copy_number_alteration_CNA',sep='\t',index_col=0)
omics3 = pd.read_csv('DataSet_OvarianCancer/RNASeq',sep='\t',index_col=0)
label = pd.read_csv('DataSet_OvarianCancer/ClinicalMatrix',sep='\t',index_col=0)
```

## Citation

If you find this method useful, please cite our paper:

```bibtex
@inproceedings{tabakhi2022multi,
  title={Multi-agent Feature Selection for Integrative Multi-omics Analysis},
  author={Tabakhi, Sina and Lu, Haiping},
  booktitle={2022 44th Annual International Conference of the IEEE Engineering in Medicine \& Biology Society (EMBC)},
  pages={1638--1642},
  year={2022},
  organization={IEEE}
  doi={10.1109/EMBC48229.2022.9871758}
}
```
