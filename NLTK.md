NLTK---
title: "NLTK"
date: 2019-04-08T22:38:04+08:00
draft: false
---
---------------------
#### 1. tokenize
https://www.nltk.org/_modules/nltk/tokenize.html

Support sentence, word, for 17 languages
source code for sentence tokenizer:
```python
def sent_tokenize(text, language='english'):
    """
    Return a sentence-tokenized copy of *text*,
    using NLTK's recommended sentence tokenizer
    (currently :class:`.PunktSentenceTokenizer`
    for the specified language).

    :param text: text to split into sentences
    :param language: the model name in the Punkt corpus
    """
    tokenizer = load('tokenizers/punkt/{0}.pickle'.format(language))
    return tokenizer.tokenize(text)
    
word tokenizer:
word_tokenize(text, language='english', preserve_line=False)
perserve_line == false, then call sentence tokenizer first, otherwise, don't
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAwODM5Mzg5MCwxODk5OTQwNTE3XX0=
-->