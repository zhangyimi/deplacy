# [deplacy](https://koichiyasuoka.github.io/deplacy/) d'anàlisi sintàctica

## amb [Camphr-Udify](https://camphr.readthedocs.io/en/latest/notes/udify.html)

```py
>>> import spacy
>>> nlp=spacy.load("en_udify")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [Stanza](https://stanfordnlp.github.io/stanza)

```py
>>> import stanza
>>> nlp=stanza.Pipeline("ca")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [NLP-Cube](https://github.com/Adobe/NLP-Cube)

```py
>>> from cube.api import Cube
>>> nlp=Cube()
>>> nlp.load("ca")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [spacy-udpipe](https://github.com/TakeLab/spacy-udpipe)

```py
>>> import spacy_udpipe
>>> nlp=spacy_udpipe.load("ca")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [UDPipe 2](http://ufal.mff.cuni.cz/udpipe/2)

```py
>>> def nlp(t):
...   import urllib.request,urllib.parse,json
...   with urllib.request.urlopen("https://lindat.mff.cuni.cz/services/udpipe/api/process?model=ca&tokenizer&tagger&parser&data="+urllib.parse.quote(t)) as r:
...     return json.loads(r.read())["result"]
...
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [spaCy-COMBO](https://github.com/KoichiYasuoka/spaCy-COMBO)

```py
>>> import spacy_combo
>>> nlp=spacy_combo.load("ca_ancora")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ ROOT
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [spaCy-jPTDP](https://github.com/KoichiYasuoka/spaCy-jPTDP)

```py
>>> import spacy_jptdp
>>> nlp=spacy_jptdp.load("ca_ancora")
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ ROOT
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [Turku-neural-parser-pipeline](https://turkunlp.org/Turku-neural-parser-pipeline/)

```py
>>> import sys,subprocess
>>> nlp=lambda t:subprocess.run([sys.executable,"full_pipeline_stream.py","--gpu","-1","--conf","models_ca_ancora/pipelines.yaml"],cwd="Turku-neural-parser-pipeline",input=t,encoding="utf-8",stdout=subprocess.PIPE).stdout
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          DET   <╗         det
tennis      NOUN  ═╝<════╗   nsubj
té          VERB  ═╗═╗═╗═╝═╗ root
avui        ADV   <╝ ║ ║   ║ advmod
a           ADP   <╗ ║ ║   ║ case
Catalunya   PROPN ═╝<╝ ║   ║ obl
molta       DET   <╗   ║   ║ det
importància NOUN  ═╝<══╝   ║ obj
.           PUNCT <════════╝ punct
```

## amb [DiaParser](https://github.com/Unipisa/diaparser)

```py
>>> from diaparser.parsers import Parser
>>> parser=Parser.load("ca_ancora.mbert")
>>> nlp=lambda t:"\n".join([str(s) for s in parser.predict(t,text="ca",prob=True).sentences])
>>> doc=nlp("El tennis té avui a Catalunya molta importància.")
>>> import deplacy
>>> deplacy.render(doc)
El          <╗         det
tennis      ═╝<════╗   nsubj
té          ═╗═╗═╗═╝═╗ root
avui        <╝ ║ ║   ║ advmod
a           <╗ ║ ║   ║ case
Catalunya   ═╝<╝ ║   ║ obl
molta       <╗   ║   ║ det
importància ═╝<══╝   ║ obj
.           <════════╝ punct
```

