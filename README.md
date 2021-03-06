## Project AutoNomic
building a decentralized platform for formally verifiable applications.
### Roadmap:
At the core is a backchaining rule engine. RDF is used as input/output format, which brings about interoperability with the Semantic Web.

The reasoning capabilities and supported forms of rules correspond to Datalog+, an extension to the well-known Datalog language.

We have gone through a series of prototypes. The latest one is called pyco, and lives in this repo alongside a growing suite of testcases.


### History

### Similar projects
http://ceptr.org/
http://qeditas.org/
https://www.tezos.com/
https://github.com/odipar/spread/
https://github.com/unisonweb/unison

AutoNomic originally started as part of project tauchain (http://www.idni.org/), and while Ohad Asor decided to pursue a different formalism (MSOL?), AutoNomic continues with the ideas of FOL + MLTT.

### pyin/pyco
the AutoNomic-pyco repo currently serves as a sort of stable branch, while development happens in "univar".
for running it, python3 is best bet, it might work with 2 with some tweaks
```
sudo apt install python3 python3-dev virtualenv clang
```
#### on ubuntu 16.4
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get install gcc-8 libc++abi-8-dev
wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|sudo apt-key add -
sudo mcedit /etc/apt/sources.list
sudo apt-get install clang-8
```
#### to set up pyco, it's best to use virtualenv:
```
virtualenv -p python3 cpython3
. cpython3/bin/activate
pip install -r pyin/requirements_pyco.txt 
```

#### then you can run it like so:
fish shell:
```
env PYTHONUNBUFFERED=1 ./pyin/tau2.py   "./pyco_runner.sh --novalgrind  true --nodebug true --oneword false  --profile false   " tests/clean/zzpanla/ldl0     2>&1 | tee runs/(date "+%F-%H-%M-%S") | tee runs/last
```
bash:
```
... `date "+%F-%H-%M-%S"` ...
```
pyco will output a trace, point your browser to the pyco_visualization directory and use , and . keys to move around the trace steps

### semantics
some notes are here: https://github.com/koo5/n3-dev-testcases

we support two forms of rules, 
1) with only universal variables
2) so called AE rules

On rules with existential variables: Walking the decidability line - https://www.sciencedirect.com/science/article/pii/S0004370211000397

RDFLog: It's like Datalog for RDF - https://www.cs.ox.ac.uk/publications/publication2719-abstract.html


### learn more
recent irc logs are at http://loworbit.now.im/logs/AutoNomic.log.txt

introduction to FOL: https://www.coursera.org/learn/logic-introduction/

one starting point for exloring semantics of n3 can be https://github.com/w3c/N3/issues

we have many more resources for anyone curious, so come say hi 
in #AutoNomic on freenode.
