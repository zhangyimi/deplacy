# Anailís ghramadaí trí [deplacy](https://koichiyasuoka.github.io/deplacy/)

## le [Stanza](https://stanfordnlp.github.io/stanza)

```py
>>> import stanza
>>> nlp=stanza.Pipeline("ga")
>>> doc=nlp("Táimid faoi dhraíocht ag ceol na farraige.")
>>> import deplacy
>>> deplacy.render(doc)
Táimid    VERB  ═══╗═══╗═╗ root
faoi      ADP   <╗ ║   ║ ║ case
dhraíocht NOUN  ═╝<╝   ║ ║ xcomp:pred
ag        ADP   <════╗ ║ ║ case
ceol      NOUN  ═══╗═╝<╝ ║ obl
na        DET   <╗ ║     ║ det
farraige  NOUN  ═╝<╝     ║ nmod
.         PUNCT <════════╝ punct
```

## le [spacy-udpipe](https://github.com/TakeLab/spacy-udpipe)

```py
>>> import spacy_udpipe
>>> nlp=spacy_udpipe.load("ga")
>>> doc=nlp("Táimid faoi dhraíocht ag ceol na farraige.")
>>> import deplacy
>>> deplacy.render(doc)
Táimid    VERB  ═══╗═══╗═╗ ROOT
faoi      ADP   <╗ ║   ║ ║ case
dhraíocht NOUN  ═╝<╝   ║ ║ xcomp:pred
ag        ADP   <════╗ ║ ║ case
ceol      NOUN  ═══╗═╝<╝ ║ obl
na        DET   <╗ ║     ║ det
farraige  NOUN  ═╝<╝     ║ nmod
.         PUNCT <════════╝ punct
```

## le [Camphr-Udify](https://camphr.readthedocs.io/en/latest/notes/udify.html)

```py
>>> from camphr.pipelines import load_udify
>>> nlp=load_udify("ga")
>>> doc=nlp("Táimid faoi dhraíocht ag ceol na farraige.")
>>> import deplacy
>>> deplacy.render(doc)
Táimid    VERB  ═══╗═══╗═╗ root
faoi      ADP   <╗ ║   ║ ║ case
dhraíocht NOUN  ═╝<╝   ║ ║ obl
ag        ADP   <════╗ ║ ║ case
ceol      NOUN  ═══╗═╝<╝ ║ obl
na        DET   <╗ ║     ║ det
farraige  NOUN  ═╝<╝     ║ compound
.         PUNCT <════════╝ punct
```

## le [NLP-Cube](https://github.com/Adobe/NLP-Cube)

```py
>>> from cube.api import Cube
>>> nlp=Cube()
>>> nlp.load("ga")
>>> doc=nlp("Táimid faoi dhraíocht ag ceol na farraige.")
>>> import deplacy
>>> deplacy.render(doc)
Táimid    VERB  ═══╗═══╗═╗ root
faoi      ADP   <╗ ║   ║ ║ case
dhraíocht NOUN  ═╝<╝   ║ ║ obl
ag        ADP   <════╗ ║ ║ case
ceol      NOUN  ═══╗═╝<╝ ║ obl
na        DET   <╗ ║     ║ det
farraige  NOUN  ═╝<╝     ║ compound
.         PUNCT <════════╝ punct
```
