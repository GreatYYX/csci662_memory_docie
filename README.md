# Reproduction of Dynamic Global Memory for Document-level Argument Extraction

This is a executable version of https://github.com/xinyadu/memory_docie.

We fixed several issues. Since the purpose was to reproduce the work, we did not improve the structure and readability of the code.

We do not know the original authors and the copyright is belong to the original authors. 

## Dependencies

Install following dependencies:

```
pytorch-lightning==1.0.6
torch==1.6.0
torchvision==0.7.0
sentence-transformers==2.1.0
transformers==4.23.1
spacy==3.0
```

Install spacy language resource:

```
spacy download en-core-web-sm
```

Install Cuda version 10.2.

## Execution 

To convert raw KAIROS data into JSON for training, testing and validation.

```
python src/genie/KAIROS_data_module.py
```

To train and test extraction model:

```
./scripts/train_kairos.sh
./scripts/test_kairos.sh
```


### Test word2vec

Uncomment the word2vec function and change SentenceTransformer related variables (e.g. `self.sim_model` to `self.wv`) in the `KAIROS_data_module.py` and `model.py`. Rerun the files to generate new JSON files for training and testing.

### Test Sentence Bert

Change pre-trained S-Bert model names in `self.sim_model` variable to test the performance of different S-Bert models.

Below is the original readme file:

# Dynamic Global Memory for Document-level Argument Extraction

Code and data for paper the ACL 22 paper ([link](http://xinyadu.github.io/papers/ACL22_Doc_level_informative_arg_extraction.pdf)).


## Dependencies 
- pytorch=1.6 
- transformers=3.1.0
- pytorch-lightning=1.0.6
- spacy=3.0 # conflicts with transformers
- pytorch-struct=0.4 
- sentence-transformers=2.1.0

## Datasets
<!-- - RAMS (Download at [https://nlp.jhu.edu/rams/]) -->
<!-- - ACE05 (Access from LDC[https://catalog.ldc.upenn.edu/LDC2006T06] and preprocessing following OneIE[http://blender.cs.illinois.edu/software/oneie/]) -->
- WikiEvents (included in this repo)


## Running


- Normal data setting

	Train:``./scripts/train_kairos.sh`` Test: ``./scripts/test_kairos.sh``

- Adversarial data setting


	Train:``./scripts/train_kairos_adv.sh`` Test: ``./scripts/test_kairos_adv.sh``
	
## Cite

If you use our code or data/outputs, please cite:

	@InProceedings{memory_ie,
	  author = {Du, Xinya and Li, Sha and Ji, Heng},
	  title = {Dynamic Global Memory for Document-level Argument Extraction},
	  booktitle = {Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics},
	  year = {2022},
	}
