# [deplacy](https://koichiyasuoka.github.io/deplacy/) pre syntaktickú analýzu

## s [Camphr-Udify](https://camphr.readthedocs.io/en/latest/notes/udify.html)

```py
>>> import spacy
>>> nlp=spacy.load("en_udify")
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  ═════╗═╗<╗   nsubj
druhému ADJ   <╗   ║ ║ ║   amod
jamu    NOUN  ═╝<╗ ║ ║ ║   obj
kope    VERB  ═══╝<╝ ║ ║   acl
sám     DET   <══════╝ ║   xcomp
do      ADP   <╗       ║   case
nej     PRON  ═╝<╗     ║   obl
spadne  VERB  ═══╝═════╝═╗ root
.       PUNCT <══════════╝ punct
```

## s [spacy-udpipe](https://github.com/TakeLab/spacy-udpipe)

```py
>>> import spacy_udpipe
>>> nlp=spacy_udpipe.load("sk")
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  ═══╗<══╗   nsubj
druhému ADJ   <╗ ║   ║   amod
jamu    NOUN  ═╝<╝   ║   obj
kope    VERB  ═╗═╗═╗═╝═╗ ROOT
sám     DET   <╝ ║ ║   ║ obl
do      ADP   <╗ ║ ║   ║ case
nej     PRON  ═╝<╝ ║   ║ obl
spadne  VERB  <════╝   ║ conj
.       PUNCT <════════╝ punct
```

## s [NLP-Cube](https://github.com/Adobe/NLP-Cube)

```py
>>> from cube.api import Cube
>>> nlp=Cube()
>>> nlp.load("sk")
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  <════════╗   nsubj
druhému ADJ   <══╗     ║   amod
jamu    DET   ═╗═╝<══╗ ║   obj
kope    NOUN  <╝     ║ ║   nmod
sám     DET   <════╗ ║ ║   obl
do      ADP   <╗   ║ ║ ║   case
nej     PRON  ═╝<╗ ║ ║ ║   obl
spadne  VERB  ═══╝═╝═╝═╝═╗ root
.       PUNCT <══════════╝ punct
```

## s [Stanza](https://stanfordnlp.github.io/stanza)

```py
>>> import stanza
>>> nlp=stanza.Pipeline("sl")
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  ═════╗<══╗   nsubj
druhému ADJ   <══╗ ║   ║   amod
jamu    NOUN  ═╗═╝ ║<╗ ║   obj
kope    NOUN  <╝   ║ ║ ║   nmod
sám     DET   <════╝ ║ ║   xcomp
do      ADP   <╗     ║ ║   case
nej     PRON  ═╝<╗   ║ ║   obl
spadne  VERB  ═══╝═══╝═╝═╗ root
.       PUNCT <══════════╝ punct
```
