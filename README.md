<div align="center">    
 
# Exploring Non-Verbal Predicates in Semantic Role Labeling: Challenges and Opportunities

<!-- [![Paper](http://img.shields.io/badge/paper-ACL--anthology-B31B1B.svg)](http://arxiv.org/abs/2307.01870) -->
[![arXiv](https://img.shields.io/badge/arXiv-2307.01870-b31b1b.svg)](https://arxiv.org/abs/2307.01870)
[![Conference](http://img.shields.io/badge/ACL-2023-4b44ce.svg)](https://2023.aclweb.org/)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

</div>

## About the project
This is the repository for the paper [*Exploring Non-Verbal Predicates in Semantic Role Labeling: Challenges and Opportunities*](http://arxiv.org/abs/2307.01870), presented at ACL 2023 by [Riccardo Orlando](https://riccardorlando.xyz/), [Simone Conia](https://c-simone.github.io/) and [Roberto Navigli](https://www.diag.uniroma1.it/navigli/).

## Abstract
Although we have witnessed impressive progress in Semantic Role Labeling (SRL), most of the research in the area is carried out assuming that the majority of predicates are verbs.
Conversely, predicates can also be expressed using other parts of speech, e.g., nouns and adjectives.
However, non-verbal predicates appear in the benchmarks we commonly use to measure progress in SRL less frequently than in some real-world settings -- newspaper headlines, dialogues, and tweets, among others.
In this paper, we put forward a new PropBank dataset which boasts wide coverage of multiple predicate types. Thanks to it, we demonstrate empirically that standard benchmarks do not provide an accurate picture of the current situation in SRL and that state-of-the-art systems are still incapable of transferring knowledge across different predicate types.
Having observed these issues, we also present a novel, manually-annotated challenge set designed to give equal importance to verbal, nominal, and adjectival predicate-argument structures. We use such dataset to investigate whether we can leverage different linguistic resources to promote knowledge transfer.
In conclusion, we claim that SRL is far from ''solved'', and its integration with other semantic tasks might enable significant improvements in the future, especially for the long tail of non-verbal predicates, thereby facilitating further research on SRL for non-verbal predicates.

## Datasets

### Download the data

You can download a copy of all the files in this repository by cloning the
[git](https://git-scm.com/) repository:

```sh
git clone https://github.com/SapienzaNLP/exploring-srl.git
```

or [download a zip archive](https://github.com/SapienzaNLP/exploring-srl/archive/main.zip).

### Data format
The data is available in a format that is very similar to the [CoNLL-U format](https://universaldependencies.org/format.html).
Here is an example:

```
# sentence_id = 109
# text = The police cordoned off the crime scene from the rest of the park .
109 	 0 	The      	-    	-      	-         	(ARG0*
109 	 1 	police   	-    	-      	-         	*)
109 	 2 	cordoned 	VERB 	cordon 	cordon.01 	*
109 	 3 	off      	-    	-      	-         	(ARGM-PRD*)
109 	 4 	the      	-    	-      	-         	(ARG1*
109 	 5 	crime    	-    	-      	-         	*
109 	 6 	scene    	-    	-      	-         	*)
109 	 7 	from     	-    	-      	-         	(ARG2*
109 	 8 	the      	-    	-      	-         	*
109 	 9 	rest     	-    	-      	-         	*
109 	10 	of       	-    	-      	-         	*
109 	11 	the      	-    	-      	-         	*
109 	12 	park     	-    	-      	-         	*)
109 	13 	.        	-    	-      	-         	*

```

* **Column 1:** sentence id in the file.
* **Column 2:** token index in the sentence.
* **Column 3:** tokens in the sentence.
* **Column 4:** pos of each token in the sentence.
* **Column 5:** lemma of each token in the sentence.
* **Column 6:** Frame of a predicate. If the token is not a predicate, then `_`.
* **Column 7 + i:** Roles of predicate `i`. E.g. Column 7 lists the roles for the first predicate, i.e., `cordoned`.

### Datasets

We release three datasets for verbal, nominal and adjectival SRL. Within the data folder, there are several sub-folders, each representing a specific dataset or category.

* The `challenge-srl` folder contains the files for the Challenge-SRL dataset. It further contains two sub-folders:

  * `propbank` referers to the dataset annotated with PropBank for different predicate types: adjectives, nouns, and verbs.
  * `verbatlas` includes instead VerbAtlas annotations for adjectives, nouns, and verbs.

* The `parallel-semlink` folder contains the files for the Parallel-Semlink dataset. A train, dev and test split is provided. It is orginized into sub-folders for each of the different linguistic inventory it includes, i.e., `framenet`, `propbank`, `verbatlas`, and `verbnet`.

* The `pb-examples` folder contains the files for the PB-Examples dataset with PropBank annotations categorized by predicate types.

* The `pb-unseen` folder contains the files for the PB-Unseen datase PropBank annotations also categorized by predicate types.

Each dataset file is stored within its corresponding folder, following a naming convention that indicates the category and type of annotations. For example, the file names often include abbreviations such as `pb` for PropBank, `fn` for FrameNet, or `va` for VerbAtlas, followed by the predicate type (e.g., `adjectives`, `nouns`, `verbs`).

```
data
├── challenge-srl
│   ├── propbank
│   │   ├── challengesrl.adjectives.pb.conllu
│   │   ├── challengesrl.all.pb.conllu
│   │   ├── challengesrl.nouns.pb.conllu
│   │   └── challengesrl.verbs.pb.conllu
│   └── verbatlas
│       ├── challengesrl.adjectives.va.conllu
│       ├── challengesrl.all.va.conllu
│       ├── challengesrl.nouns.va.conllu
│       └── challengesrl.verbs.va.conllu
├── parallel-semlink
│   ├── framenet
│   │   ├── parallelsemlink.fn.dev.conllu
│   │   ├── parallelsemlink.fn.test.conllu
│   │   └── parallelsemlink.fn.train.conllu
│   ├── propbank
│   │   ├── parallelsemlink.pb.dev.conllu
│   │   ├── parallelsemlink.pb.test.conllu
│   │   └── parallelsemlink.pb.train.conllu
│   ├── verbatlas
│   └── verbnet
│       ├── parallelsemlink.vn.dev.conllu
│       ├── parallelsemlink.vn.test.conllu
│       └── parallelsemlink.vn.train.conllu
├── pb-examples
│   ├── pbexamples.adjectives.conllu
│   ├── pbexamples.all.conllu
│   ├── pbexamples.nouns.conllu
│   └── pbexamples.verbs.conllu
└── pb-unseen
    ├── pbunseen.adjectives.conllu
    ├── pbunseen.all.conllu
    ├── pbunseen.nouns.conllu
    └── pbunseen.verbs.conllu
```

#### PB-Examples and PB-Unseen

PB-Examples is a new evaluation benchmark for comprehensively evaluate different predicate types. To build PB-Examples, we collect the examples sentences provided with each predicate in PropBank 3 ([Palmer et al., 2005](https://direct.mit.edu/coli/article/31/1/71/1861/The-Proposition-Bank-An-Annotated-Corpus-of); [Pradhan et al., 2022](https://aclanthology.org/2022.starsem-1.24/)). In the table below we report statistics on the coverage of CoNLL-2009 ([Hajič et al., 2009](https://aclanthology.org/W09-1201/)), OntoNotes 5.0 ([Pradhan et al., 2022](https://aclanthology.org/2022.starsem-1.24/)) and PB-Examples in terms of unique framesets (rightmost column).
Compared to its alternatives, PB-Examples covers 7481 unique PropBank framesets against 2490 framesets covered in the OntoNotes test set and 2427 in CoNLL-2009.
Moreover, when comparing PB-Examples to OntoNotes, the number of unique framesets used in verbal predicate occurrences is more than double (5465 vs. 2215), whereas it is almost double for nominal occurrences (1384 vs. 782).
Adjectival occurrences are essentially missing in OntoNotes (with 3 unique framesets only), while PB-Examples covers 1599.

We also release  PB-unseen, a more challenge subset of PB-Examples which features predicate senses that are not included in OntoNotes 5.0.

|          | Verbs | Nouns | Adjs | Framesets |
|----------|-------|-------|------|-----------|
| CoNLL-2009      | 1090  | 1337  | 0    | 2427      |
| OntoNotes 5.0   | 2215  | 782   | 3    | 2490      |
| PB-Examples   | 5465  | 1384  | 1599 | 7481      |
| PB-Unseen     | 2457  | 469   | 1389 | 4001      |

#### Parallel-SemLink

Parallel-SemLink is a multi-inventory benchmark made up of the subset of OntoNotes from SemLink 2.0 ([Stowe et al., 2021](https://aclanthology.org/2021.iwcs-1.21/)), whose predicates and arguments are annotated with PropBank, FrameNet ([Baker et al., 1998](https://dl.acm.org/doi/10.3115/980845.980860)), and VerbNet ([Schuler and Palmer, 2005](https://repository.upenn.edu/dissertations/AAI317980)).
It also includes VerbAtlas ([Di Fabio et al., 2019](https://aclanthology.org/D19-1058/)) annotations thanks to the inter-resource mapping between VerbNet, WordNet, and VerbAtlas.
For each of these inventories, Parallel-SemLink includes a training, a validation, and a test set with 7336, 816, and 906 sentences, respectively.

#### Challenge-SRL

Challenge-SRL is a manually-annotated test-set for verbal, nominal and adjectival predicates that features parallel labels for PropBank and VerbAtlas. This dataset only features predicate-argument structures that do not appear in OntoNotes. Therefore, Challenge-SRL is useful to measure the capability of an SRL system to generalize i) across predicate types, and ii) on the long tail of predicate senses.

To construct Challenge-SRL, we randomly selected a total of 288 sentences -- 96 sentences for each predicate type -- from PB-Unseen.
We then asked three expert annotators to independently annotate each sentence with predicate senses and their semantic roles.
The annotation process was carried out in two phases: first, each person annotated each sentence independently, resulting in a disagreement of 32%; then, the annotators discussed and resolved their disagreements, if possible, reducing them to 6%.
Overall, Challenge-SRL includes 1898 predicate-argument pairs.

## Cite this work
If you use any part of this work, please consider citing the paper as follows:

```bibtex
@inproceedings{orlando-etal-2023-exploring-srl,
    title     = "Exploring Non-Verbal Predicates in Semantic Role Labeling: Challenges and Opportunities",
    author    = "Orlando, Riccardo and Conia, Simone and Navigli, Roberto",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2023",
    month     = jul,
    year      = "2023",
    address   = "Toronto, Canada",
    publisher = "Association for Computational Linguistics",
}
```

## License
The data is licensed under [Creative Commons Attribution-ShareAlike 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
