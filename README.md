### Repository of the **_add_** paper: [A Hierarchical Label Network for Multi-Label EuroVoc Classification of Legislative Contents]()

- BibTeX:

## Overview
This repository contains EUR-Lex PT, a large scale and multi-label dataset with more than 220k documents, labeled under the three EuroVoc hierarchical levels. The dataset is available with the original division in training (64%), validation (16%), and test (20%) sub-sets. The training, validation and test sets have 140883, 35189 and 44254 documents, respectively, and the entire corpus has a vocabulary with 42556 words.

We also added the source code of our hierarchical deep learning model (HLAN) to address the classification of legal documents according to the EuroVoc thesaurus. Instead of training a classifier for each level, our model allows the simultaneous prediction of the three levels of the EuroVoc thesaurus.

## Classifier

**Installation**
1. Please, install the packages listed on the ```requirements.txt``` file. 

    1.1 Run ```virtualenv -p python3 envname```

    1.2 Run ```envname/bin/pip install -r requirements.txt```

2. Download CBOW 300 dimensions (cbow_s300.zip) from [NILC-Embeddings](http://143.107.183.175:22980/download.php?file=embeddings/wang2vec/cbow_s300.zip) and unzip it to ```data/embeddings/``` directory.

3. Download the pre-processed EUR-Lex-PT dataset ```clean_txt_withallwords.json``` from [here](https://drive.google.com/file/d/1f2nIAL5Ef30vPeMi4j2YOpChQBcaJUQA/view?usp=sharing) to ```data/``` directory.

4. Run ```classifier/hierarchical.py```.


## Data

### EUR-Lex-PT

The pre-processed EUR-Lex-PT is formated with a JSON representation as follows: 

```
{   
    "celex": "eur-lex_identifier", 
    "url": "eur-lex_url",
    "eurovoc_ids": ["descriptor_index_1", "descriptor_index_2", ..., "descriptor_index_n"], 
    "eurovoc_mts": ["micro-thesaurus_index_1", "micro-thesaurus_index_2", ..., "micro-thesaurus_index_n"],
    "eurovoc_dom": ["domain_index_1", "domain_index_2", ..., "domain_index_n"], 
    "txt": "document_text"
}
```

**Note:** The documents' sentences (```"txt"``` field) are separated by a ```__SENT__``` delimiter.



### EUR-Lex-PT LIBSVM format

The EUR-Lex-PT corpus is also available under the LIBSVM format at [EUR-Lex-PT LIBSVM](https://drive.google.com/file/d/1u2BCJRH-BC4l9wCgRoDkLnGGvj9fwj5d/view?usp=sharing): 

- Each LIBSVM file contains a header in the format:

```<#instances> <#features> <#classes>```

- The other lines of the LIBSVM files are in the format:

```<label> <index1>:<value1> <index2>:<value2> ...```


### EuroVoc Thesaurus

The EuroVoc thesaurus can be found at the ```data/eurovoc.json``` file. Each descriptor is organized according to the structure presented bellow. As the descriptors may contain equivalent terms (preferred and non-preferred), we list all these terms under the ```terms``` list.

```
"descriptor_index": {
        "id": "descriptor_index",
        "terms": [
            "descriptor_label_1",
            "descriptor_label_2",
        ],
        "preferred_term": "descriptor_label",
        "micro-thesauri": {
            "micro-thesaurus_index_1": "micro-thesaurus_label_1",
            "micro-thesaurus_index_2": "micro-thesaurus_label_2"
        },
        "domains": {
            "domain_index_1": "domain_index_1",
            "domain_index_2": "domain_index_2",
        }
    }
 ```

## Contact

I am happy answer questions and give additional information via email: dcaled at gmail dot com
