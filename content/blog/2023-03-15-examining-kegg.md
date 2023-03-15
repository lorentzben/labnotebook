---
title: 'Examining Kegg'
date: 2023-03-15T14:32:56Z
draft: false
meta_img: "images/image.png"
tags:
  - "huang2018"
  - "Kegg"
  - "peptidase"
description: "Description for the page"
---

### Todos for Today

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- gg-catalog
  - Find out which Kegg genes are involved in Nitrogen Metabolism
    - examine printed pathways
  - Generate a gene network 
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community

### gg-catalog

#### What genes are involved in nitrogen metabolism

ko04974 Protein Digestion and Absorption 

K06002  	pepsin A [EC:3.4.23.1]
K01312  	trypsin [EC:3.4.21.4]
K01310  	chymotrypsin [EC:3.4.21.1]
K09632  	chymotrypsin-like protease [EC:3.4.21.-]
K01346  	pancreatic elastase II [EC:3.4.21.71]
K01345  	pancreatic endopeptidase E [EC:3.4.21.70]
K08779  	carboxypeptidase A1 [EC:3.4.17.1]
K01298  	carboxypeptidase A2 [EC:3.4.17.15]
K08780  	carboxypeptidase A3 [EC:3.4.17.1]
K01291  	carboxypeptidase B [EC:3.4.17.2]
K01300  	carboxypeptidase B2 [EC:3.4.17.20]
K12040  	solute carrier family 9 (sodium/hydrogen exchanger), member 3
K14206  	solute carrier family 15 (oligopeptide transporter), member 1
K01539  	sodium/potassium-transporting ATPase subunit alpha [EC:7.2.2.13]
K01540  	sodium/potassium-transporting ATPase subunit beta
K01538  	sodium/potassium-transporting ATPase subunit gamma (FXYD domain-containing ion transport regulator 2)
K04945  	potassium intermediate/small conductance calcium-activated channel subfamily N member 4
K04916  	potassium channel subfamily K member 5
K04897  	potassium voltage-gated channel Isk-related subfamily E member 3
K04926  	potassium voltage-gated channel KQT-like subfamily member 1
K05006  	potassium inwardly-rectifying channel subfamily J member 13
K14207  	solute carrier family 38 (sodium-coupled neutral amino acid transporter), member 2
K01389  	neprilysin [EC:3.4.24.11]
K01395  	meprin A [EC:3.4.24.18]
K08606  	meprin B [EC:3.4.24.63]
K09708  	angiotensin-converting enzyme 2 [EC:3.4.17.23]
K01285  	lysosomal Pro-X carboxypeptidase [EC:3.4.16.2]
K01278  	dipeptidyl-peptidase 4 [EC:3.4.14.5]
K14208  	Xaa-Pro aminopeptidase 2 [EC:3.4.11.9]
K05612  	solute carrier family 1 (neuronal/epithelial high affinity glutamate transporter), member 1
K05616  	solute carrier family 1 (neutral amino acid transporter), member 5
K05849  	solute carrier family 8 (sodium/calcium exchanger)
K05334  	solute carrier family 6 (neurotransmitter transporter) member 19
K06519  	solute carrier family 3, member 2
K13781  	solute carrier family 7 (L-type amino acid transporter), member 8
K14209  	solute carrier family 36 (proton-coupled amino acid transporter)
K08187  	MFS transporter, MCT family, solute carrier family 16 (monocarboxylic acid transporters), member 10
K14210  	solute carrier family 3 (neutral and basic amino acid transporter), member 1
K13868  	solute carrier family 7 (L-type amino acid transporter), member 9/15
K13867  	solute carrier family 7 (L-type amino acid transporter), member 7
K14211  	***elastin***
K06236  	***collagen type I alpha***
K19719  	collagen type II alpha
K19720  	collagen type III alpha
K06237  	collagen type IV alpha
K19721  	collagen type V/XI/XXIV/XXVII, alpha
K06238  	collagen type VI alpha
K16628  	collagen type VII alpha
K23455  	collagen type VIII alpha
K08131  	collagen type IX alpha
K19479  	collagen type X alpha
K08132  	collagen type XII alpha
K16617  	collagen type XIII alpha
K08133  	collagen type XIV alpha
K08135  	collagen type XV alpha
K24339  	collagen type XVI alpha
K07603  	collagen type XVII alpha
K06823  	collagen type XVIII alpha
K24340  	collagen type XIX alpha
K24357  	collagen type XX alpha
K16629  	collagen type XXI alpha
K16630  	collagen type XXII alpha
K24355  	collagen type XXIII alpha
K24356  	collagen type XXV alpha
K24358  	collagen type XXVI alpha (EMI domain-containing protein 2)
K23619    ***collagen type XXVIII alpha***

ko00280 Valine, leucine, and isoleucine degradation 

 	
K00826  	branched-chain amino acid aminotransferase [EC:2.6.1.42]
K03334  	L-amino-acid oxidase [EC:1.4.3.2]
K00271  	valine dehydrogenase (NAD+) [EC:1.4.1.23]
K00263  	leucine dehydrogenase [EC:1.4.1.9]
K00166  	2-oxoisovalerate dehydrogenase E1 component alpha subunit [EC:1.2.4.4]
K00167  	2-oxoisovalerate dehydrogenase E1 component beta subunit [EC:1.2.4.4]
K11381  	2-oxoisovalerate dehydrogenase E1 component [EC:1.2.4.4]
K09699  	2-oxoisovalerate dehydrogenase E2 component (dihydrolipoyl transacylase) [EC:2.3.1.168]
K00382  	dihydrolipoamide dehydrogenase [EC:1.8.1.4]
K00186  	2-oxoisovalerate ferredoxin oxidoreductase alpha subunit [EC:1.2.7.7]
K00187  	2-oxoisovalerate ferredoxin oxidoreductase beta subunit [EC:1.2.7.7]
K00189  	2-oxoisovalerate/pyruvate ferredoxin oxidoreductase gamma subunit [EC:1.2.7.7 1.2.7.1]
K00188  	2-oxoisovalerate ferredoxin oxidoreductase delta subunit [EC:1.2.7.7]
K00248  	butyryl-CoA dehydrogenase [EC:1.3.8.1]
K00249  	acyl-CoA dehydrogenase [EC:1.3.8.7]
K00253  	isovaleryl-CoA dehydrogenase [EC:1.3.8.4]
K11410  	short-chain 2-methylacyl-CoA dehydrogenase [EC:1.3.8.5]
K09478  	short-chain 2-methylacyl-CoA dehydrogenase [EC:1.3.8.5]
K11538  	isobutyryl-CoA dehydrogenase [EC:1.3.99.-]
K01692  	enoyl-CoA hydratase [EC:4.2.1.17]
K01825  	3-hydroxyacyl-CoA dehydrogenase / enoyl-CoA hydratase / 3-hydroxybutyryl-CoA epimerase / enoyl-CoA isomerase [EC:1.1.1.35 4.2.1.17 5.1.2.3 5.3.3.8]
K01782  	3-hydroxyacyl-CoA dehydrogenase / enoyl-CoA hydratase / 3-hydroxybutyryl-CoA epimerase [EC:1.1.1.35 4.2.1.17 5.1.2.3]
K07515  	enoyl-CoA hydratase / long-chain 3-hydroxyacyl-CoA dehydrogenase [EC:4.2.1.17 1.1.1.211]
K07514  	enoyl-CoA hydratase / 3-hydroxyacyl-CoA dehydrogenase / 3,2-trans-enoyl-CoA isomerase [EC:4.2.1.17 1.1.1.35 5.3.3.8]
K07511  	enoyl-CoA hydratase [EC:4.2.1.17]
K00022  	3-hydroxyacyl-CoA dehydrogenase [EC:1.1.1.35]
K08683  	3-hydroxyacyl-CoA dehydrogenase / 3-hydroxy-2-methylbutyryl-CoA dehydrogenase [EC:1.1.1.35 1.1.1.178]
K00632  	acetyl-CoA acyltransferase [EC:2.3.1.16]
K07513  	acetyl-CoA acyltransferase 1 [EC:2.3.1.16]
K07508  	acetyl-CoA acyltransferase 2 [EC:2.3.1.16]
K07509  	acetyl-CoA acyltransferase [EC:2.3.1.16]
K01965  	propionyl-CoA carboxylase alpha chain [EC:6.4.1.3]
K01966  	propionyl-CoA carboxylase beta chain [EC:6.4.1.3 2.1.3.15]
K11263  	acetyl-CoA/propionyl-CoA carboxylase, biotin carboxylase, biotin carboxyl carrier protein [EC:6.4.1.2 6.4.1.3 6.3.4.14]
K18472  	acetyl-CoA/propionyl-CoA carboxylase carboxyl transferase subunit [EC:6.4.1.2 6.4.1.3 2.1.3.15]
K19312  	acetyl-CoA/propionyl-CoA carboxylase carboxyl transferase subunit [EC:6.4.1.2 6.4.1.3 2.1.3.15]
K22568  	acetyl-CoA/propionyl-CoA carboxylase, PccX subunit [EC:6.4.1.2 6.4.1.3]
K01964  	acetyl-CoA/propionyl-CoA carboxylase [EC:6.4.1.2 6.4.1.3]
K15036  	acetyl-CoA/propionyl-CoA carboxylase [EC:6.4.1.2 6.4.1.3 2.1.3.15]
K15037  	biotin carboxyl carrier protein
K05606  	methylmalonyl-CoA/ethylmalonyl-CoA epimerase [EC:5.1.99.1]
K01847  	methylmalonyl-CoA mutase [EC:5.4.99.2]
K01849  	methylmalonyl-CoA mutase, C-terminal domain [EC:5.4.99.2]
K01848  	methylmalonyl-CoA mutase, N-terminal domain [EC:5.4.99.2]
K05605  	3-hydroxyisobutyryl-CoA hydrolase [EC:3.1.2.4]
K00020  	3-hydroxyisobutyrate dehydrogenase [EC:1.1.1.31]
K23146  	3-hydroxyisobutyrate/3-hydroxypropionate dehydrogenase [EC:1.1.1.31 1.1.1.59]
K00140  	malonate-semialdehyde dehydrogenase (acetylating) / methylmalonate-semialdehyde dehydrogenase [EC:1.2.1.18 1.2.1.27]
K00128  	aldehyde dehydrogenase (NAD+) [EC:1.2.1.3]
K14085  	aldehyde dehydrogenase family 7 member A1 [EC:1.2.1.31 1.2.1.8 1.2.1.3]
K00149  	aldehyde dehydrogenase family 9 member A1 [EC:1.2.1.47 1.2.1.3]
K00157  	aldehyde oxidase [EC:1.2.3.1]
K18660  	malonyl-CoA/methylmalonyl-CoA synthetase [EC:6.2.1.76 6.2.1.-]
K18661  	malonyl-CoA/methylmalonyl-CoA synthetase [EC:6.2.1.76 6.2.1.-]
K00822  	beta-alanine--pyruvate transaminase [EC:2.6.1.18]
K07250  	4-aminobutyrate aminotransferase / (S)-3-amino-2-methylpropionate transaminase / 5-aminovalerate transaminase [EC:2.6.1.19 2.6.1.22 2.6.1.48]
K13524  	4-aminobutyrate aminotransferase / (S)-3-amino-2-methylpropionate transaminase [EC:2.6.1.19 2.6.1.22]
K00827  	alanine-glyoxylate transaminase / (R)-3-amino-2-methylpropionate-pyruvate transaminase [EC:2.6.1.44 2.6.1.40]
K01968  	3-methylcrotonyl-CoA carboxylase alpha subunit [EC:6.4.1.4]
K01969  	3-methylcrotonyl-CoA carboxylase beta subunit [EC:6.4.1.4]
K05607  	methylglutaconyl-CoA hydratase [EC:4.2.1.18]
K13766  	methylglutaconyl-CoA hydratase [EC:4.2.1.18]
K01640  	hydroxymethylglutaryl-CoA lyase [EC:4.1.3.4]
K01027  	3-oxoacid CoA-transferase [EC:2.8.3.5]
K01028  	3-oxoacid CoA-transferase subunit A [EC:2.8.3.5]
K01029  	3-oxoacid CoA-transferase subunit B [EC:2.8.3.5]
K01907  	acetoacetyl-CoA synthetase [EC:6.2.1.16]
K00626  	acetyl-CoA C-acetyltransferase [EC:2.3.1.9]
K01641  	hydroxymethylglutaryl-CoA synthase [EC:2.3.3.10]

 	
ko00350 Tyrosine metabolism

K14454  	aspartate aminotransferase, cytoplasmic [EC:2.6.1.1]
K14455  	aspartate aminotransferase, mitochondrial [EC:2.6.1.1]
K00811  	aspartate aminotransferase, chloroplastic [EC:2.6.1.1]
K00812  	aspartate aminotransferase [EC:2.6.1.1]
K00813  	aspartate aminotransferase [EC:2.6.1.1]
K11358  	aspartate aminotransferase [EC:2.6.1.1]
K15849  	bifunctional aspartate aminotransferase and glutamate/aspartate-prephenate aminotransferase [EC:2.6.1.1 2.6.1.78 2.6.1.79]
K00815  	tyrosine aminotransferase [EC:2.6.1.5]
K00817  	histidinol-phosphate aminotransferase [EC:2.6.1.9]
K00832  	aromatic-amino-acid transaminase [EC:2.6.1.57]
K00838  	aromatic amino acid aminotransferase I / 2-aminoadipate transaminase [EC:2.6.1.57 2.6.1.39 2.6.1.27 2.6.1.5]
K05821  	aromatic amino acid aminotransferase II [EC:2.6.1.58 2.6.1.28]
K00270  	phenylalanine dehydrogenase [EC:1.4.1.20]
K03334  	L-amino-acid oxidase [EC:1.4.3.2]
K00457  	4-hydroxyphenylpyruvate dioxygenase [EC:1.13.11.27]
K00451  	homogentisate 1,2-dioxygenase [EC:1.13.11.5]
K01800  	maleylacetoacetate isomerase [EC:5.2.1.2]
K01555  	fumarylacetoacetase [EC:3.7.1.2]
K16171  	fumarylacetoacetate (FAA) hydrolase [EC:3.7.1.2]
K00422  	polyphenol oxidase [EC:1.10.3.1]
K00505  	tyrosinase [EC:1.14.18.1]
K00501  	tyrosine 3-monooxygenase [EC:1.14.16.2]
K24287  	L-tyrosine peroxygenase [EC:1.11.2.6]
K01827  	dopachrome tautomerase [EC:5.3.3.12]
K22203  	dopachrome tautomerase [EC:5.3.3.12]
K00506  	tyrosinase-related protein 1 [EC:1.14.18.-]
K22329  	tyrosine decarboxylase [EC:4.1.1.25]
K01592  	tyrosine decarboxylase [EC:4.1.1.25]
K22330  	tyrosine decarboxylase [EC:4.1.1.25]
K18933  	tyrosine decarboxylase / aspartate 1-decarboxylase [EC:4.1.1.25 4.1.1.11]
K01593  	aromatic-L-amino-acid/L-tryptophan decarboxylase [EC:4.1.1.28 4.1.1.105]
K00503  	dopamine beta-monooxygenase [EC:1.14.17.1]
K00553  	phenylethanolamine N-methyltransferase [EC:2.1.1.28]
K00545  	catechol O-methyltransferase [EC:2.1.1.6]
K00274  	monoamine oxidase [EC:1.4.3.4]
K00276  	primary-amine oxidase [EC:1.4.3.21]
K13371  	aralkylamine dehydrogenase light chain [EC:1.4.9.2]
K13372  	aralkylamine dehydrogenase heavy chain [EC:1.4.9.2]
K25271  	tyramine oxidase subunit A [EC:1.4.3.-]
K25272  	tyramine oxidase subunit B [EC:1.4.3.-]
K01618  	3,4-dihydroxyphenylacetaldehyde synthase [EC:4.1.1.107]
K00129  	aldehyde dehydrogenase (NAD(P)+) [EC:1.2.1.5]
K00146  	phenylacetaldehyde dehydrogenase [EC:1.2.1.39]
K13951  	alcohol dehydrogenase 1/7 [EC:1.1.1.1]
K13980  	alcohol dehydrogenase 4 [EC:1.1.1.1]
K00121  	S-(hydroxymethyl)glutathione dehydrogenase / alcohol dehydrogenase [EC:1.1.1.284 1.1.1.1]
K13952  	alcohol dehydrogenase 6 [EC:1.1.1.1]
K04072  	acetaldehyde dehydrogenase / alcohol dehydrogenase [EC:1.2.1.10 1.1.1.1]
K13953  	alcohol dehydrogenase, propanol-preferring [EC:1.1.1.1]
K13954  	alcohol dehydrogenase [EC:1.1.1.1]
K18857  	alcohol dehydrogenase class-P [EC:1.1.1.1]
K00001  	alcohol dehydrogenase [EC:1.1.1.1]
K22327  	4-hydroxyphenylacetaldehyde synthase [EC:4.1.1.108]
K00483  	4-hydroxyphenylacetate 3-monooxygenase [EC:1.14.14.9]
K23492  	4-hydroxyphenylacetate 3-monooxygenase [EC:1.14.14.9]
K16901  	anthranilate 3-monooxygenase (FAD) / 4-hydroxyphenylacetate 3-monooxygenase [EC:1.14.14.8 1.14.14.9]
K00484  	flavin reductase (NADH) [EC:1.5.1.36]
K23470  	4-hydroxyphenylacetate 3-hydroxylase, reductase component [EC:1.5.1.36]
K16902  	FAD reductase [NAD(P)H] [EC:1.5.1.45]
K00455  	3,4-dihydroxyphenylacetate 2,3-dioxygenase [EC:1.13.11.15]
K00151  	5-carboxymethyl-2-hydroxymuconic-semialdehyde dehydrogenase [EC:1.2.1.60]
K10219  	2-hydroxy-4-carboxymuconate semialdehyde hemiacetal dehydrogenase [EC:1.1.1.312]
K01826  	5-carboxymethyl-2-hydroxymuconate isomerase [EC:5.3.3.10]
K05921  	5-oxopent-3-ene-1,2,5-tricarboxylate decarboxylase / 2-hydroxyhepta-2,4-diene-1,7-dioate isomerase [EC:4.1.1.68 5.3.3.-]
K02509  	2-oxo-hept-3-ene-1,7-dioate hydratase [EC:4.2.1.-]
K02510  	4-hydroxy-2-oxoheptanedioate aldolase [EC:4.1.2.52]
K00135  	succinate-semialdehyde dehydrogenase / glutarate-semialdehyde dehydrogenase [EC:1.2.1.16 1.2.1.79 1.2.1.20]
K01668  	tyrosine phenol-lyase [EC:4.1.99.2]
K10774  	tyrosine ammonia-lyase [EC:4.3.1.23]
K00431  	thyroid peroxidase [EC:1.11.1.8]
K00055  	aryl-alcohol dehydrogenase [EC:1.1.1.90]
K00157  	aldehyde oxidase [EC:1.2.3.1]
K00450  	gentisate 1,2-dioxygenase [EC:1.13.11.4]
K01801  	maleylpyruvate isomerase [EC:5.2.1.4]
K16163  	maleylpyruvate isomerase [EC:5.2.1.4]
K01557  	acylpyruvate hydrolase [EC:3.7.1.5]
K16164  	acylpyruvate hydrolase [EC:3.7.1.5]
K16165  	fumarylpyruvate hydrolase [EC:3.7.1.20]
K20758  	maleylpyruvate hydrolase [EC:3.7.1.23]
K07253  	phenylpyruvate tautomerase [EC:5.3.2.1]
K23109  	aromatic 2-oxoacid reductase [EC:1.1.1.110]
K18606  	hydroxyphenylpyruvate reductase [EC:1.1.1.237]
K13574  	hydroxycarboxylate dehydrogenase B [EC:1.1.1.237 1.1.1.-]
K21425  	rosmarinate synthase [EC:2.3.1.140]

 	
ko00380 Tryptophan Metabolism 

K00453  	tryptophan 2,3-dioxygenase [EC:1.13.11.11]
K00463  	indoleamine 2,3-dioxygenase [EC:1.13.11.52]
K01432  	arylformamidase [EC:3.5.1.9]
K14263  	kynurenine formamidase [EC:3.5.1.9]
K07130  	arylformamidase [EC:3.5.1.9]
K00486  	kynurenine 3-monooxygenase [EC:1.14.13.9]
K01556  	kynureninase [EC:3.7.1.3]
K16901  	anthranilate 3-monooxygenase (FAD) / 4-hydroxyphenylacetate 3-monooxygenase [EC:1.14.14.8 1.14.14.9]
K16902  	FAD reductase [NAD(P)H] [EC:1.5.1.45]
K00452  	3-hydroxyanthranilate 3,4-dioxygenase [EC:1.13.11.6]
K03392  	aminocarboxymuconate-semialdehyde decarboxylase [EC:4.1.1.45]
K23234  	aminomuconate-semialdehyde dehydrogenase [EC:1.2.1.32]
K10217  	aminomuconate-semialdehyde/2-hydroxymuconate-6-semialdehyde dehydrogenase [EC:1.2.1.32 1.2.1.85]
K15067  	2-aminomuconate deaminase [EC:3.5.99.5]
K15791  	probable 2-oxoglutarate dehydrogenase E1 component DHKTD1 [EC:1.2.4.2]
K00658  	2-oxoglutarate dehydrogenase E2 component (dihydrolipoamide succinyltransferase) [EC:2.3.1.61]
K00382  	dihydrolipoamide dehydrogenase [EC:1.8.1.4]
K00252  	glutaryl-CoA dehydrogenase [EC:1.3.8.6]
K01692  	enoyl-CoA hydratase [EC:4.2.1.17]
K01825  	3-hydroxyacyl-CoA dehydrogenase / enoyl-CoA hydratase / 3-hydroxybutyryl-CoA epimerase / enoyl-CoA isomerase [EC:1.1.1.35 4.2.1.17 5.1.2.3 5.3.3.8]
K01782  	3-hydroxyacyl-CoA dehydrogenase / enoyl-CoA hydratase / 3-hydroxybutyryl-CoA epimerase [EC:1.1.1.35 4.2.1.17 5.1.2.3]
K07515  	enoyl-CoA hydratase / long-chain 3-hydroxyacyl-CoA dehydrogenase [EC:4.2.1.17 1.1.1.211]
K07514  	enoyl-CoA hydratase / 3-hydroxyacyl-CoA dehydrogenase / 3,2-trans-enoyl-CoA isomerase [EC:4.2.1.17 1.1.1.35 5.3.3.8]
K07511  	enoyl-CoA hydratase [EC:4.2.1.17]
K00022  	3-hydroxyacyl-CoA dehydrogenase [EC:1.1.1.35]
K00626  	acetyl-CoA C-acetyltransferase [EC:2.3.1.9]
K00816  	kynurenine---oxoglutarate transaminase / cysteine-S-conjugate beta-lyase / glutamine---phenylpyruvate transaminase [EC:2.6.1.7 4.4.1.13 2.6.1.64]
K00825  	kynurenine/2-aminoadipate aminotransferase [EC:2.6.1.7 2.6.1.39]
K14264  	kynurenine aminotransferase [EC:2.6.1.7]
K01667  	tryptophanase [EC:4.1.99.1]
K00502  	tryptophan 5-monooxygenase [EC:1.14.16.4]
K01593  	aromatic-L-amino-acid/L-tryptophan decarboxylase [EC:4.1.1.28 4.1.1.105]
K22433  	L-tryptophan decarboxylase [EC:4.1.1.105]
K24541  	tryptamine 5-hydroxylase [EC:1.14.-.-]
K00274  	monoamine oxidase [EC:1.4.3.4]
K00128  	aldehyde dehydrogenase (NAD+) [EC:1.2.1.3]
K14085  	aldehyde dehydrogenase family 7 member A1 [EC:1.2.1.31 1.2.1.8 1.2.1.3]
K00149  	aldehyde dehydrogenase family 9 member A1 [EC:1.2.1.47 1.2.1.3]
K00157  	aldehyde oxidase [EC:1.2.3.1]
K00543  	acetylserotonin O-methyltransferase [EC:2.1.1.4]
K00669  	arylalkylamine N-acetyltransferase [EC:2.3.1.87]
K22450  	aralkylamine N-acetyltransferase [EC:2.3.1.87]
K22588  	acetylserotonin O-methyltransferase, plant [EC:2.1.1.4]
K13066  	caffeic acid 3-O-methyltransferase / acetylserotonin O-methyltransferase [EC:2.1.1.68 2.1.1.4]
K07408  	cytochrome P450 family 1 subfamily A1 [EC:1.14.14.1]
K07409  	cytochrome P450 family 1 subfamily A2 [EC:1.14.14.1]
K07410  	cytochrome P450 family 1 subfamily B1 [EC:1.14.14.1]
K14338  	cytochrome P450 / NADPH-cytochrome P450 reductase [EC:1.14.14.1 1.6.2.4]
K00562  	methyltransferase [EC:2.1.1.49 2.1.1.96]
K11812  	tryptophan N-monooxygenase [EC:1.14.14.156]
K11813  	tryptophan N-monooxygenase [EC:1.14.14.156]
K11816  	indole-3-pyruvate monooxygenase [EC:1.14.13.168]
K03334  	L-amino-acid oxidase [EC:1.4.3.2]
K14265  	tryptophan aminotransferase [EC:2.6.1.27]
K00838  	aromatic amino acid aminotransferase I / 2-aminoadipate transaminase [EC:2.6.1.57 2.6.1.39 2.6.1.27 2.6.1.5]
K16903  	L-tryptophan---pyruvate aminotransferase [EC:2.6.1.99]
K00837  	aromatic aminotransferase [EC:2.6.1.-]
K23109  	aromatic 2-oxoacid reductase [EC:1.1.1.110]
K04103  	indolepyruvate decarboxylase [EC:4.1.1.74]
K11182  	diamine oxidase [EC:1.4.3.22]
K11868  	indoleacetaldoxime dehydratase [EC:4.8.1.3]
K11817  	indole-3-acetaldehyde oxidase [EC:1.2.3.7]
K22417  	benzaldehyde dehydrogenase (NAD+) / indole-3-acetaldehyde oxidase [EC:1.2.1.28 1.2.3.7]
K01501  	nitrilase [EC:3.5.5.1]
K01721  	nitrile hydratase subunit alpha [EC:4.2.1.84]
K20807  	nitrile hydratase subunit beta [EC:4.2.1.84]
K00466  	tryptophan 2-monooxygenase [EC:1.13.12.3]
K01426  	amidase [EC:3.5.1.4]
K21801  	indoleacetamide hydrolase [EC:3.5.1.-]
K11818  	aromatic aldoxime N-monooxygenase [EC:1.14.14.45]
K11819  	S-alkyl-thiohydroximate lyase SUR1 [EC:4.4.1.-]
K11820  	N-hydroxythioamide S-beta-glucosyltransferase [EC:2.4.1.195]
K11821  	aromatic desulfoglucosinolate sulfotransferase [EC:2.8.2.24]
K01237  	myrosinase [EC:3.2.1.147]
K03781  	catalase [EC:1.11.1.6]
K03782  	catalase-peroxidase [EC:1.11.1.21]
K20219  	o-aminophenol oxidase [EC:1.10.3.4]
K20204  	grixazone synthase / o-aminophenol oxidase [EC:1.10.3.15 1.10.3.4]
K23947  	2-oxoglutarate-dependent dioxygenase [EC:1.14.11.-]
K23384  	indoleacetate decarboxylase [EC:4.1.1.115]


I want to look into the genes that produce SCFAs 

There are some duplicate entries in the of interest table ^ 

I want to merge the selected keggs by abundance

### Todos for Tomorrow

- Jackwood Blast
  - meet Ben and Brian TBD
  - try out a local blast search to see memory, cpu time limitation
- Reply to Ade
- gg-catalog
  - compare abundances of genes of interest (gene and kegg tables)
  - Generate a gene network 
    - how do you do this?
  - query the KO list and cross ref to the abundance data
  - Find a Shotgun Analysis involved with chickens and some kind of phenotypic data.
- Generate a Mock community M&M or other and validate pipelines
- Visualize Ampliseq
  - benchmark with a mock community


### Git Commits

#### Lab Notebook

```bash
0dabddb - Benjamin Lorentz, Wed Mar 15 11:53:56 2023 -0400 : added kegg ontologies
3f5d6ab - Benjamin Lorentz, Wed Mar 15 10:34:14 2023 -0400 : added page for wednesday
9b330d8 - Benjamin Lorentz, Tue Mar 14 17:01:29 2023 -0400 : final updates for friday
```

#### gg-catalog

```bash
e30bca2 - Benjamin Lorentz, Wed Mar 15 16:52:24 2023 -0400 : update 03_huang_kegg_examine.rmd
607d65a - Benjamin Lorentz, Tue Mar 14 16:58:38 2023 -0400 : update code/03_huang_kegg_examine.sh
```