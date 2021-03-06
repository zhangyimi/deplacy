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

## s [UDPipe 2](http://ufal.mff.cuni.cz/udpipe/2)

```py
>>> def nlp(t):
...   import urllib.request,urllib.parse,json
...   with urllib.request.urlopen("https://lindat.mff.cuni.cz/services/udpipe/api/process?model=sk&tokenizer&tagger&parser&data="+urllib.parse.quote(t)) as r:
...     return json.loads(r.read())["result"]
...
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  <════╗     nsubj
druhému ADJ   <╗   ║     amod
jamu    NOUN  ═╝<╗ ║     obj
kope    VERB  ═══╝═╝<╗   advcl
sám     DET   <════╗ ║   xcomp
do      ADP   <╗   ║ ║   case
nej     PRON  ═╝<╗ ║ ║   obl
spadne  VERB  ═══╝═╝═╝═╗ root
.       PUNCT <════════╝ punct
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

## s [spaCy-COMBO](https://github.com/KoichiYasuoka/spaCy-COMBO)

```py
>>> import spacy_combo
>>> nlp=spacy_combo.load("sk_snk")
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  <══════╗   nsubj
druhému ADJ   <╗     ║   amod
jamu    NOUN  ═╝<╗   ║   nmod
kope    NOUN  ═╗═╝<╗ ║   obj
sám     DET   <╝   ║ ║   xcomp
do      ADP   <╗   ║ ║   case
nej     PRON  ═╝<╗ ║ ║   obl
spadne  VERB  ═══╝═╝═╝═╗ ROOT
.       PUNCT <════════╝ punct
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

## s [Turku-neural-parser-pipeline](https://turkunlp.org/Turku-neural-parser-pipeline/)

```py
>>> import sys,subprocess
>>> nlp=lambda t:subprocess.run([sys.executable,"full_pipeline_stream.py","--gpu","-1","--conf","models_sk_snk/pipelines.yaml"],cwd="Turku-neural-parser-pipeline",input=t,encoding="utf-8",stdout=subprocess.PIPE).stdout
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     PRON  <════════╗   nsubj
druhému ADJ   <══╗     ║   amod
jamu    NOUN  ═╗═╝<══╗ ║   obl
kope    NOUN   ║<══╗ ║ ║   obl
sám     DET   <╝   ║ ║ ║   xcomp
do      ADP   <╗   ║ ║ ║   case
nej     PRON  ═╝<╗ ║ ║ ║   obl
spadne  VERB  ═══╝═╝═╝═╝═╗ root
.       PUNCT <══════════╝ punct
```

## s [DiaParser](https://github.com/Unipisa/diaparser)

```py
>>> from diaparser.parsers import Parser
>>> parser=Parser.load("sk_snk.mbert")
>>> nlp=lambda t:"\n".join([str(s) for s in parser.predict(t,text="sk",prob=True).sentences])
>>> doc=nlp("Kto druhému jamu kope sám do nej spadne.")
>>> import deplacy
>>> deplacy.render(doc)
Kto     <════╗     mark
druhému <╗   ║     amod
jamu    ═╝<╗ ║     obl
kope    ═╗═╝═╝<╗   advcl
sám     <╝     ║   xcomp
do      <╗     ║   case
nej     ═╝<╗   ║   obl
spadne  ═══╝═══╝═╗ root
.       <════════╝ punct
```

