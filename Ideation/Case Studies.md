### Pathway Analysis

CASE STUDY 1

Loss of ASH1L in developing brains causes autistic-like behaviors in a mouse model 

BACKGROUND

Autism spectrum disorder (ASD) is a neurodevelopmental disease associated with various gene mutations. Recent genetic and clinical studies report that mutations of the epigenetic gene ASH1L are highly associated with human ASD and intellectual disability (ID). However, the causal link between ASH1L mutations and ASD/ID remains undetermined. 

HYPOTHESIS/PROBLEM STATEMENT 

ASH1L is an epigenetic factor that regulates gene expression during development. To identify the genes regulated by ASH1L in developing brains, we performed RNA-sequencing (RNA-seq) analyses to examine differential gene expression between wild-type and Ash1L-deleted neural cells.

WORKFLOW

The NPCs (neural progenitor cell)were isolated from the subventricular zone (SVZ) of brains and maintained in serum-free NPC culture medium. The deletion of Ash1L gene in the established NPCs was induced by 4-hydrotamoxifen (4OH-TAM) added in the medium for 10 days(mouse model).

To identify the differentially expressed genes in early NPC differentiation, we performed RNA-seq analyses 0, 12 and 24 hours after induced differentiation.

Results

DGE:The results identified total 2,475 upregulated and 2,808 downregulated genes during induced differentiation (cutoff: fold changes > 1.5, p < 0.01)

Gene ontology (GO) enrichment analyses showed the upregulated genes had enriched GO terms involving nervous system development, while the downregulated genes involved metabolic processes and cell cycle regulation (cutoff: FDR < 0.05) (Figure S3J-K, Table S1, S2). Among all 2,475 genes upregulated in the wild-type NPC differentiation, 70 genes were found to have significantly reduced expression in the Ash1L-KO cells (cutoff: fold changes > 1.5, p < 0.01) These genes downregulated in the Ash1L-KO cells had enriched GO terms involving telencephalon development, regulation of cell communication, brain development, and central nervous development (cutoff: FDR < 0.05) 

Reactome pathway enrichment analysis: Revealed involvement in postsynaptic signal transmission, including NMDA receptor activation (cutoff: FDR < 0.05). Notably, multiple genes, such as Emx2, Dbx2, Pcdh10, and Foxg1, that were previously reported to play critical roles in normal brain development and related neurodevelopmental diseases were found to have significantly reduced expression in the differentiating Ash1L-KO cells (cutoff: fold changes > 1.5, p < 0.01) (Figure 4D), suggesting that loss of ASH1L's function in activating genes critical for normal brain development might be a possible molecular mechanism linking ASH1L mutations to neurodevelopmental defects of ASD/ID.

INFERENCE

In this study, we used an animal model to demonstrate that the loss of Ash1L gene alone in developing mouse brains is sufficient to cause autistic-like behaviors and ID-like deficits in adult mice, which strongly suggests ASH1L gene mutations found in patients are likely to be the causative drivers leading to clinical ASD/ID.

Data Formats and Platform:

The RNA-seq data presented in this study has been deposited to the Gene Expression Omnibus database, GEO accession: GSE173262. Other data have been disclosed in the sections above, or are available from the corresponding author upon reasonable request.

CASE STUDY 2

PyGNA: a unified framework for geneset network analysis

Aim

Analysis of RNA sequencing data generated by The Cancer Genome Atlas (TCGA) project for 6 different types of cancer: 4 epithelial tumors, including 2 from urogenital tissues (BLCA and PRAD), 1 from breast (BRCA) and 1 from lung (LUSC), and 2 from liquid cancers (LAML and DLBC)

To  find whether differentially expressed genes in each cancer show a network effect, and whether they are similar to any other cancer analysed. It is possible to address these questions using the GNT and GNA tests implemented in PyGNA.

Workflow/methodology

TCGA data was retrieved  and differential expression analysis (DEA) was performed using the TCGABiolinks package. 

Data Platforms:  Gene expression data from the Genotype-Tissue EXpression (GTEX) project as control-no control for  LUSC, LAML, and DLBC, and the TCGA tumor data processed by the Recount2 project to avoid biases introduced by different RNA quantification pipelines..Taken together, we retrieved 6 datasets providing mRNA abundance for ≈15000 genes for each tumor and performed differential expression analysis. For each dataset, all genes with FDR<0.01 and logFC|>3 were considered significant.
ANALYSES 

GNT and GNA are based on three models:

-   Direct interaction model

-   Shortest path interaction model

-   Random Walk with Restart (RWR) model

These three interaction models capture different topological properties. Direct models provide information about the neighborhood of a gene and its observed links. However, they might not be sufficiently powered to detect mid- and long-range interactions, thus statistics defined under these models are usually sensitive to missing links. Conversely, modelling gene interactions using shortest path provides a simple analytical framework to include local and global awareness of the connectivity. However, this approach is also sensitive to missing links and small-world effects, which is common in biological networks and could lead to false positives. The RWR model is more robust than the shortest path model, because it effectively adjusts interaction effects for network structure; it rewards nodes connected with many shortest paths, and penalizes those that are connected only by path going through high degree nodes.

The the strength of interaction between genes in the geneset (geneset network topology, GNT) and with genes in another geneset (geneset network association, GNA) are evaluated based on statistics using these model. 

GNT Statistics:

Let S=s1,...,sn be a geneset of n genes, each mapped to a node in G=(V,E). The aim is to find out whether the strength of interaction between nodes of the geneset is higher than expected by chance for a geneset of the same size.

-   Total degree statistic: The importance of a geneset S can be quantified as the number of edges connecting each node in S to any other node in the network

    ![](https://lh4.googleusercontent.com/TFBxV9JakouiKx5a1UpJZcm30tI2cJot38B2D9jIsryM76_82NAG16gkJ9yus5BbxBAi_VydD-Eogi0HfhofssBRaLnHhkD57hdpny5CqauiMDCJ381CtquDXBwMFILPF66XiDjl)

-   Internal degree: With the direct interaction model, the strength of interaction for a geneset S can be quantified as the number of edges connecting each node in S to any other node in the geneset; we refer to this quantity as the internal degree of the node
    ![](https://lh3.googleusercontent.com/sWv5p9S3ZWHEqAN23L-VEj6UQSqHK7n-9TrZuktzsuorEgVMoyZ1F1axdYG3D5CxppMKx60vVnmFUWrs62iOdGpTGLY0g_Qe8LGnGzwTP-ntX640Kq_6UTkIPTwKPB4oLCeRScWr)
-   Shortest Path: The main concern regarding direct interaction methods is that they could fail in presence of missing links, which can be circumvented by shortest path method which takes into account the distance between nodes. Shortest path is the average of the minimum distance between each gene and the rest of those in S:

  ![](https://lh6.googleusercontent.com/0aAzF-yJwTV_GyQaCUti3iXS9tC9PSpB5zIukWBo-suYxs6AcOqVjpeggTJAr4y2pNtQRR3H41l9zfKQGUNzEMurSf5hMyNjQy7Ndi8kCQDKyFkepq2WJemiNO5vxfzxC7mUElIQ)

-   Under a RWR model, we can consider hij∈H as the heat transferred from node i to node j, which can be used as a measure of interaction strength between the nodes in the geneset S, as follows:

   ![](https://lh3.googleusercontent.com/R29kXbSK4gGjzcTDGOrv5vZX9vPOlv5LNjqBDh7cAyNZt4JJm2vpi6PgCiCP89SyjSg3EDjQWnfVm36MOoM2AqKzbNfRMK0zV6JxI9hknWgqDrUxkNLs0LwNmDOlDXP3KchLOPrh)

Geneset network association statistics

Let S1 and S2 be two geneset with n and m genes respectively, we want to estimate the association between S1 and S2 as a function of the strength of interaction between their nodes.

Under a shortest path model, the association statistics USP is defined as follows:

Whereas, under a RWR model, we measure association as a function of the heat, UH, transferred between the two genesets as follows:

![](https://lh4.googleusercontent.com/pNFrWarxqb1BktJC4aWQCBtDERjy0DshwL03xuSeeanyFcNeGjuixsXbQtnyoZZsTqtqVOvz4zqf_CQaKYuzwlRczG9XFADGZ1bXnUXgN7xcxBC5Zga6wC9FccWHZuoPGsrMFTKQ)

Where the heat withheld by a gene is considered when there are overlapping genes between S1 and S2.
![](https://lh6.googleusercontent.com/9WUqYLEtoYJjwofcsQPPfIPv0xlfGsmODfhA7ETtZmtQ0ZewVP_oOnmwBmmTaQd2a0lTchhJtSuDcqoQ2nL1--UqAe866plxRMfNHI88Eg1KOBQIbPTznpyi-Hw4Q48OgiwGxYzl)

Hypothesis Testing

The topological and association statistics are ultimately used for hypothesis testing. A calibrated null distribution is needed to estimate whether the observed statistics are more extreme than what expected by chance using which, a bootstrap procedure is used to estimate null distributions of the test statistics, conditioned on the geneset size.

Thus, w.l.o.g, let Q be the null distribution of the test statistic q estimated for a geneset of size n, and ![](https://lh4.googleusercontent.com/XJeK67eNboaq0tH-m5YCWtbET8SYrlDwEE559PatIXDWxggXY3WwwJPgagrYaRvQECK60wSYx5sPIO_PTjRAtNy9dvx51BEQ1Kaa-B8ObW4yU3agKvjWESljd9pArBnCAGtuEEdv) the observed value. It is possible to derive an empirical p-value as follows:

 ![](https://lh6.googleusercontent.com/dU4jhvcZn0hQBFLBkB50iFBS_OVim_dfuZz8pqUPAMrejNFxl7lqcK3ques3HUgqlcPVcUb8soPwDMlQwZwXuxjNKdzf1axvkfcCwEVbrBTqdqBYjRDt5fF-n7fqTBM0ULZ7Enj8)

where I is the indicator function returning 1 if and only if the evaluated condition is true, and unit pseudo-count is added for continuity correction.

Benchmarking geneset network tests                  

Stochastic block models (SBM) was used for both GNA and GNT. 

SBM framework is used to simulate a network with k blocks, with a baseline probability of interaction within and between blocks, p0.

GNT:  k+<k blocks from the SBM matrix are selected  and set their within probability of connection M+ii = αp0, where α>1 is a scaling factor controlling the strength of interaction of the genes within block i compared to the rest of the genes in any other block.

GNA: k+  blocks are selected at random and set their within block connection probability to M+ii=αp0 and their between blocks connection to M+ij=γp0 for i≠j and α,γ>1. γ  was reparameterized as a function α, in order to control the relationship between the within and between block connection probability. 

Let β=γ/(α-1), the between block connection probability can be set as M+ij=p0+βp0(α-1). With this parametrization, 3 different scenarios can be simulated:

1)if β=0⇒M+ij=p0, the connection probability between blocks is equal to the baseline, thus genes in a block are highly connected.

2)if 0<β<1⇒p0<M+ij<M+ii, then the connection probability between the blocks is higher than the baseline, and thus we obtain assortative genesets.

3)if β>1⇒M+ij>M+ii, then we have non assortative genesets, thus we expect them to be detected by a GNA test.

After building a network, genesets can be generated by selecting two distinct blocks, i, j, with m nodes each, and add π×m nodes from block i and (1-π)×m nodes from block j; for simplicity, we picked genes from blocks containing the same number of genes. 

By varying the size of highly connected blocks and their interaction probability, along with the geneset composition, it is possible to assess the true positive rate (TPR) and false positive rate (FPR) of both GNT and GNA tests.    

USE CASE

PyGNA was used to perform GNT analysis and GNA analysis between all cancer datasets, using the BioGRID interaction network.

For each test, PyGNA returns the results as a CSV file, which includes descriptive statistics and the parameters of the null distribution used for hypothesis testing.  PyGNA plotting tool (paint-summary-gnt) twas used o visualize a summary of the GNT results for all datasets,  where the test statistic was reported as a z-score, to make them comparable across different tests.GNA analysis between all differentially expressed genesets was performed using the command (paint-comparison-matrix) in PyGNA.

RESULTS

GNT: Only differentially expressed genes in lung and lymphoid cancers show a significant network effect, albeit this is detected by all tests for lung cancer and only by TH and TID lymphoid neoplasm. 

Network effect wasn't observed for the other cancers; this could be explained by the fact these cancers might be controlled not by one highly connected network, but by multiple distinct ones.

PyGNA diagnostic plot generated by the GNT analysis-network effect detected

GNA: While most of them do not seem to show a consistent network effect, GNA can be used to test whether each set of differentially expressed genes are more connected with each other than expected by chance.Using either UH and USP tests, a significant association between breast, bladder, and prostate carcinomas, and between leukemia and lymphoid neoplasms was observed which is consistent with other gene expression analyses, that have shown that anatomically related cancers or with similar histopathology share similar changes in gene expression.

Significant association between lung and lymphoid neoplasms observed in the study might be explained by the fact that lungs contain a vast lymphatic network, which might also be dysregulated in lung tumors.

Conclusion: PyGNA enables network analysis of RNA sequencing datasets and provide useful biological insights about the association between the genes.

CASE STUDY 3

In silico Pathway Activation Network Decomposition Analysis (iPANDA) as a method for biomarker development

BACKGROUND

The inherent complexity of gene network interactions and high diversity of experimental platforms and inconsistency of the data coming from the various types of equipment pose a major challenge in analysing transcriptomics data posing a need for the development of the new large-scale analytical methodologies that infer complex transcriptomic changes more accurately into the network of biologically relevant signalling axes.

Breast cancer data was chosen for the analysis as one of the most challenging in several ways. Since breast cancer has a high degree of intertumour and intratumoural heterogeneity, this cancer type is one of the most difficult in terms of outcome and treatment response prediction. This is especially true for a group of tumours with poor prognosis and fewer number of effective treatments. Thus, traditional methods for transcriptomic data analysis may not be sufficient in this particular case.

The aim is to show that iPANDA is capable of producing highly robust sets of pathway markers, which can be further used for stratification of samples into responder and non-responder groups using neoadjuvant therapy pretreatment breast cancer data with known treatment outcome and receptor status (estrogen receptor and HER2). 

Data Availability and Platform

Six data sets containing gene expression data related to breast cancer patients treated with paclitaxel and three data sets containing transcriptomic data from normal cancer-free breast tissue which were used as a reference from GEO.The MicroArray Quality Control (MAQC) data set (GEO identifier 5350) was obtained from the GEO database.

Platforms: Affymetrix, Agilent

Algorithm

-   The topological weight of each gene is proportional to the number of independent paths through the pathway gene network represented as a directed graph.

-   The computation of topological coefficients for a set of coexpressed genes is inefficient, unless a group of coexpressed genes is being considered as a single unit. To circumvent this challenge, gene modules reflecting the coexpression of genes are introduced in the iPANDA algorithm. 

-   The contribution of gene units (including gene modules and individual genes) to pathway activation is computed as a product of their fold changes in logarithmic scale, topological and statistical weights. Then the contributions are multiplied by a discrete coefficient which equals to +1 or -1 in the case of pathway activation or suppression by the particular unit, respectively. Finally, the activation scores, which we refer to as iPANDA values, are obtained as a linear combination of the scores calculated for gene units that contribute to the pathway activation/suppression. 

### Biomarker identification and relevance: Methodology and Results

-   Measure receiver operating characteristics area under curve (AUC) values to assess the capability of transcriptomic pathway markers to distinguish between two groups of samples: 

-   Gene expression data sets from breast cancer patients with measured response to paclitaxel treatment

-   Pathway activation scores for each sample obtained

-   Lists of the top 30 paclitaxel treatment sensitivity pathway markers obtained for the estrogen receptor negative (ERN) HER2-positive (HER2P) and ERN HER2-negative (HER2N) breast cancer types were obtained.

-   Four and five independent data sets were used for comparison of ERN HER2P and ERN HER2N cancer types

-   Ranked based on AUC values

-   The lists of markers differ significantly between cancer types--complies with the observation that the mechanisms of paclitaxel treatment resistance depend on the breast cancer subtype

-   Produces consistent results for different data sets obtained independently for the same biological case--iPANDA values for 19 and 8 pathways for ERN HER2P and ERN HER2N breast cancer types, respectively, can be utilized as paclitaxel response classifiers with AUC values higher than 0.7 for all data sets examined

-   The common marker pathway (CMP) index to estimate the robustness of the biomarker lists: the combined implementation of the gene modules along with the topology-based coefficients serves as an effective way of noise reduction in gene expression data and allows one to obtain stable pathway activation scores for a set of independent data

-   Pathway activation scores obtained using iPANDA were applied to the identification of paclitaxel neoadjuvant therapy sensitivity in breast cancer: the models developed using normalized iPANDA scores distinguished paclitaxel treatment responders from non-responders with high accuracy

Conclusions

Application of the pathway activation measurement implemented in iPANDA leads to significant noise reduction in the input data to produce highly consistent sets of biologically relevant biomarkers acquired on multiple transcriptomic data sets. More robust since it takes both gene expression and pathway activation into account since they both have their unique insights to offer from the context of a disease.

REFERENCES

1.  <https://genomebiology.biomedcentral.com/articles/10.1186/s13059-019-1790-4>

2.  <https://advaitabio.com/ipathwayguide/pathway-analysis-vs-gene-set-analysis/>

3.  <https://www.frontiersin.org/articles/10.3389/fphys.2015.00383/full>

4.  <https://www.nature.com/articles/s41467-019-13983-9>

5.  <https://academic.oup.com/nar/article/49/W1/W114/6284183>
