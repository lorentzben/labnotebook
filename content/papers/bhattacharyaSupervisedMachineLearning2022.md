---
title: bhattacharyaSupervisedMachineLearning2022
author: ''
date: '2022-10-24'
slug: ['sheets2022']
categories: []
tags:
  - one tag
  - another tag
meta_img: images/image.png
description: Description for the page
---

# Supervised Machine Learning Enables Geospatial Microbial Provenance
#### (2022) - Chandrima Bhattacharya, Braden T. Tierney, Krista A. Ryon, Malay Bhattacharyya, Jaden J. A. Hastings, Srijani Basu, Bodhisatwa Bhattacharya, Debneel Bagchi, Somsubhro Mukherjee, Lu Wang, Elizabeth M. Henaff, Christopher E. Mason
- **Link**:: https://www.mdpi.com/2073-4425/13/10/1914
- **DOI**:: 10.3390/genes13101914
- **Links**:: 
- **Tags**:: #paper
- **Cite Key**:: [@bhattacharyaSupervisedMachineLearning2022] 

### Abstract
The recent increase in publicly available metagenomic datasets with geospatial metadata has made it possible to determine location-specific, microbial fingerprints from around the world. Such fingerprints can be useful for comparing microbial niches for environmental research, as well as for applications within forensic science and public health. To determine the regional specificity for environmental metagenomes, we examined 4305 shotgun-sequenced samples from the MetaSUB Consortium dataset—the most extensive public collection of urban microbiomes, spanning 60 different cities, 30 countries, and 6 continents. We were able to identify city-specific microbial fingerprints using supervised machine learning (SML) on the taxonomic classifications, and we also compared the performance of ten SML classifiers. We then further evaluated the five algorithms with the highest accuracy, with the city and continental accuracy ranging from 85–89% to 90–94%, respectively. Thereafter, we used these results to develop Cassandra, a random-forest-based classifier that identifies bioindicator species to aid in fingerprinting and can infer higher-order microbial interactions at each site. We further tested the Cassandra algorithm on the Tara Oceans dataset, the largest collection of marine-based microbial genomes, where it classified the oceanic sample locations with 83% accuracy. These results and code show the utility of SML methods and Cassandra to identify bioindicator species across both oceanic and urban environments, which can help guide ongoing efforts in biotracing, environmental monitoring, and microbial forensics (MF).

### Notes
<h1>Annotations
 (11/16/2022, 8:58:13 PM)</h1> 

“Outside of humanassociated ecosystems, microbial forensics (MF) could feasibly be used—in the oceans, for example—for tracking deleterious algal blooms or organisms with unknown migration patterns [14]. This would be complementary to existing approaches in which oceanographers use discarded host DNA to ascertain the presence of a given species [15].” (Bhattacharya et al., 2022, p. 2) 

“The goal of microbial forensics is to be able to identify the point of origin, provenance, or likely history of any given sample using microbial fingerprints: distinct microbiomes that can identify their place of origin [16].” (Bhattacharya et al., 2022, p. 2) 

“Additionally, Segata et al., 2011, developed Linear Discriminant Analysis (LDA) effect size (LEfSe) method and used LDA-based methods for finding biomarkers, including phenotypic indicators from 16S samples [21].” (Bhattacharya et al., 2022, p. 2) 

“Ideally, metagenomic datasets could be used to develop discriminating microbial signatures or fingerprints, but there is a lack of universally accepted tools for identifying bioindicator species from metagenomics data [10,23].” (Bhattacharya et al., 2022, p. 2) 

“Here, we present Cassandra, an SML tool to address these unmet needs of metagenomicsbased microbial forensics, which can predict bioindicator species from shotgun sequence datasets.” (Bhattacharya et al., 2022, p. 3) 

“We chose to use a Random Forest because it yields output that is simple to interpret, stable against Gaussian noise, does not overfit in unbalanced datasets, and the standard deviation between the various preprocessor methods is extremely low.” (Bhattacharya et al., 2022, p. 5) 

“Cassandra first does an 80–20 train-test split, creates a new tree based on the training set, and trains the model. It evaluates the accuracy of the test set. If the desired accuracy is achieved, Cassandra selects the run and reports the attributed features (microbes) for the run. The algorithm keeps running till we have 1000 instances to achieve consensus (which can be modified by users) with the desired accuracy. The weight of all the species is reported for each of those instances, which helps us understand higher-level interaction between species and the geolocation. Furthermore, another output file is generated which selects the top n-species of interest (which can be user modifiers) of interest which are bioindicator species.” (Bhattacharya et al., 2022, p. 5) 

“We next examined the output of Cassandra after this processing, which details the weight associated with each microbe for classification with minimum accuracy. We found that microbial abundance (the amount of a given microbe) and microbial prevalence (the number of samples where the microbes were found) had a linear relationship (Figure 3A).” (Bhattacharya et al., 2022, p. 9) 

“Out of the 31 core microbial taxa in the MetaSUB dataset, we observed 4 of them in the top 50 bioindicator species, namely: Streptococcus mitis, Brevundimonas sp. GW460, Brevundimonas naejangsanensis, Cutibacterium acnes.” (Bhattacharya et al., 2022, p. 9) 

“Using the MetaSUB dataset, we next examined the ability to predict other forensic features, including surface material (e.g., metal, glass, plastic), temperature, climate, and other clues of sample provenance. To develop these methods, we trained the MetaSUB species data on eight unique features, including surface type, sampling type, coastal city, climate, and others (Table 3). Each feature was analyzed independently using 3 crossvalidation methods (k-fold, leave one group out for the city, and one for the continent), which repeatedly uses part of the samples for learning the model, and the remainder for validating the predictions (Methods 2.3).” (Bhattacharya et al., 2022, p. 9) 

“In general, microbial data can also classify other associated features with geolocation, like elevation, coastal association, and climate. To confirm this, we also tested classification with LOGO, where we also saw some features like surface material (coarse) outperforming k-fold validation.” (Bhattacharya et al., 2022, p. 9) 

“In general, we found that we were able to predict all taxon levels, with a precision and recall of greater than 65% (Figure 4), including Operational Taxonomic Units (OTUs). For class, genus, and OTU, the accuracy was greater than 80%. We then used OTUs to train Cassandra, which achieved 86.5% accuracy (the top 15 bioindicators’ OTUs are depicted in Figure 4B).” (Bhattacharya et al., 2022, p. 9) 

“This investigation demonstrates that, even from varied mixtures of microbial communities, we can uniquely predict the provenance of a given metagenomic sample by its microbial fingerprint.” (Bhattacharya et al., 2022, p. 12) 

“Deploying the MetaSUB protocol [4], we were able to classify the continent and city of origin from a given WGS metagenomic sample from the global dataset, with 94% and 89% accuracy, respectively, and the sea or ocean of origin with 83% accuracy when using OTUs from the Tara Oceans dataset.” (Bhattacharya et al., 2022, p. 12) 

“Species classified by Cassandra can be further used to monitor pathogenic outbreaks as well as the spread of” (Bhattacharya et al., 2022, p. 12) 

“AMR using additional resources. Databases like Global Biodiversity Information Facility (GBIF) [49], TerrestrialMetagenomeDB [50], and Microbe Directory (MD2) [51] can be used as ancillary information for defining phenotypes, and other attributes of the bioindicators species [52].” (Bhattacharya et al., 2022, p. 13) 

“Further applications include tracking the microbiome before and after exposure to diseases like SARS COV2 [57], and determining changes in the microibial composition following dietary alterations [58–60].” (Bhattacharya et al., 2022, p. 13) 

“However, such use requires caution, as it could contribute to errors, socioeconomic discrimination, or stigmatization, and the results would need to be verified, as with all other methods in forensics. Nonetheless, the tools, data, and methods are finally emerging to make such methods of tracking and provenance a reality.” (Bhattacharya et al., 2022, p. 13)