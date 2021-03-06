# Analysis syntaxis super [deplacy](https://koichiyasuoka.github.io/deplacy/)

## per [spaCy-COMBO](https://github.com/KoichiYasuoka/spaCy-COMBO)

```py
>>> import spacy_combo
>>> nlp=spacy_combo.load("la_ittb")
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    NOUN  <══════════╗   obj
amet    VERB  ═══════╗═╗═╝═╗ ROOT
qui     PRON  <══╗   ║ ║   ║ nsubj
numquam ADV   <╗ ║   ║ ║   ║ advmod:emph
amavit  VERB  ═╝═╝═╗<╝ ║   ║ csubj
,       PUNCT <════╝   ║   ║ punct
quique  PRON  <════╗   ║   ║ nsubj
amavit  VERB  ═══╗═╝<══╝   ║ csubj
cras    NOUN  <╗ ║         ║ obj
amet    VERB  ═╝<╝         ║ ccomp
.       PUNCT <════════════╝ punct
```

## per [Stanza](https://stanfordnlp.github.io/stanza)

```py
>>> import stanza
>>> nlp=stanza.Pipeline("la")
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    PRON  <══════════════╗   nsubj
amet    VERB  ═════════════╗═╝═╗ root
qui     PRON  <══════════╗ ║   ║ nsubj
numquam ADV   <╗         ║ ║   ║ advmod:emph
amavit  VERB  ═╝═══════╗═╝<╝   ║ ccomp
,       PUNCT <══════╗ ║       ║ punct
quique  PRON  <════╗ ║ ║       ║ nsubj
amavit  VERB  ═╗═╗═╝═╝<╝       ║ conj
cras    PRON  <╝ ║             ║ obj
amet    VERB  <══╝             ║ ccomp
.       PUNCT <════════════════╝ punct
```

## per [UDPipe 2](http://ufal.mff.cuni.cz/udpipe/2)

```py
>>> def nlp(t):
...   import urllib.request,urllib.parse,json
...   with urllib.request.urlopen("https://lindat.mff.cuni.cz/services/udpipe/api/process?model=la&tokenizer&tagger&parser&data="+urllib.parse.quote(t)) as r:
...     return json.loads(r.read())["result"]
...
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    NOUN  ═════╗<══╗     nsubj
amet    VERB  ═══════╗═╝═╗═╗ root
qui     PRON  <══╗ ║ ║   ║ ║ nsubj
numquam ADV   <╗ ║ ║ ║   ║ ║ advmod:emph
amavit  VERB  ═╝═╝<╝ ║   ║ ║ acl:relcl
,       PUNCT <══╗   ║   ║ ║ punct
quique  PRON  <╗ ║   ║   ║ ║ obj
amavit  VERB  ═╝═╝<══╝   ║ ║ ccomp
cras    NOUN  <╗         ║ ║ obj
amet    VERB  ═╝<════════╝ ║ conj
.       PUNCT <════════════╝ punct
```

## per [spacy-udpipe](https://github.com/TakeLab/spacy-udpipe)

```py
>>> import spacy_udpipe
>>> nlp=spacy_udpipe.load("la")
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    PROPN ═╗═════╗<╗   nsubj
amet    PRON  <╝     ║ ║   det
qui     PRON  <══╗   ║ ║   nsubj
numquam ADV   <╗ ║   ║ ║   advmod
amavit  VERB  ═╝═╝═╗<╝ ║   acl:relcl
,       PUNCT <════╝   ║   punct
quique  ADV   <════╗   ║   advmod
amavit  VERB  ═══╗═╝═══╝═╗ ROOT
cras    NOUN  <╗ ║       ║ obj
amet    VERB  ═╝<╝       ║ ccomp
.       PUNCT <══════════╝ punct
```

## per [Camphr-Udify](https://camphr.readthedocs.io/en/latest/notes/udify.html)

```py
>>> import spacy
>>> nlp=spacy.load("en_udify")
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    NOUN  ═════╗<╗         nsubj
amet    VERB  ═══════╝═╗═╗═╗═╗ root
qui     PRON  <══╗ ║   ║ ║ ║ ║ nsubj
numquam ADV   <╗ ║ ║   ║ ║ ║ ║ advmod
amavit  VERB  ═╝═╝<╝   ║ ║ ║ ║ acl
,       PUNCT <════════╝ ║ ║ ║ punct
quique  PRON  <╗         ║ ║ ║ nsubj
amavit  VERB  ═╝<════════╝ ║ ║ conj
cras    ADV   <╗           ║ ║ advmod
amet    VERB  ═╝<══════════╝ ║ conj
.       PUNCT <══════════════╝ punct
```

## per [NLP-Cube](https://github.com/Adobe/NLP-Cube)

```py
>>> from cube.api import Cube
>>> nlp=Cube()
>>> nlp.load("la")
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    NOUN  ═════════════╗<╗   obj
amet    VERB  ═══════════════╝═╗ root
qui     PRON  <════════╗   ║   ║ nsubj
numquam ADV   <╗       ║   ║   ║ advmod:emph
amavit  VERB  ═╝═════╗═╝═╗<╝   ║ acl
,       PUNCT <════╗ ║   ║     ║ punct
quique  PRON  <══╗ ║ ║   ║     ║ nsubj
amavit  VERB     ║ ║<╝   ║     ║ conj
cras    NOUN  <╗ ║ ║     ║     ║ obj
amet    VERB  ═╝═╝═╝<════╝     ║ conj
.       PUNCT <════════════════╝ punct
```

## per [Turku-neural-parser-pipeline](https://turkunlp.org/Turku-neural-parser-pipeline/)

```py
>>> import sys,subprocess
>>> nlp=lambda t:subprocess.run([sys.executable,"full_pipeline_stream.py","--gpu","-1","--conf","models_la_ittb/pipelines.yaml"],cwd="Turku-neural-parser-pipeline",input=t,encoding="utf-8",stdout=subprocess.PIPE).stdout
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    NOUN  <════════════╗   obj
amet    VERB  ═══════════╗═╝═╗ root
qui     PRON  <══════╗   ║   ║ nsubj
numquam PRON  <╗     ║   ║   ║ advmod
amavit  VERB  ═╝═══╗═╝═╗<╝   ║ ccomp
,       PUNCT <══╗ ║   ║     ║ punct
quique  PRON  <╗ ║ ║   ║     ║ obj
amavit  VERB  ═╝═╝<╝   ║     ║ conj
cras    NOUN  <╗       ║     ║ obj
amet    VERB  ═╝<══════╝     ║ conj
.       PUNCT <══════════════╝ punct
```

## per [DiaParser](https://github.com/Unipisa/diaparser)

```py
>>> from diaparser.parsers import Parser
>>> parser=Parser.load("la_ittb_llct.mbert")
>>> nlp=lambda t:"\n".join([str(s) for s in parser.predict(t,text="la",prob=True).sentences])
>>> doc=nlp("Cras amet qui numquam amavit, quique amavit cras amet.")
>>> import deplacy
>>> deplacy.render(doc)
Cras    ═════╗<════╗   nsubj
amet    ═════════╗═╝═╗ root
qui     <══╗ ║   ║   ║ nsubj
numquam <╗ ║ ║   ║   ║ advmod:emph
amavit  ═╝═╝<╝   ║   ║ acl:relcl
,       <══════╗ ║   ║ punct
quique  <════╗ ║ ║   ║ mark
amavit  ═╗═╗═╝═╝<╝   ║ ccomp
cras    <╝ ║         ║ obj
amet    <══╝         ║ ccomp
.       <════════════╝ punct
```

