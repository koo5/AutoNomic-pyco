##Project AutoNomic
building a decentralized platform for formally verifiable applications.
#Roadmap:
At the core is a backchaining rule engine. RDF is used as input/output format, which brings about interoperability with the Semantic Web.

The reasoning capabilities and supported forms of rules correspond to Datalog+, an extension to the well-known Datalog language.

We have gone through a series of prototypes. The latest one is called pyco, and lives in this repo alongside a growing suite of testcases.


#History

#Similar projects
http://ceptr.org/
http://qeditas.org/
https://www.tezos.com/
https://github.com/odipar/spread/
https://github.com/unisonweb/unison




## pyin/pyco
#python3 is best bet, it might work with 2 with some tweaks
sudo apt install python3 python3-dev virtualenv clang

#on ubuntu 16.4
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get install gcc-8 libc++abi-8-dev
wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|sudo apt-key add -
sudo mcedit /etc/apt/sources.list
sudo apt-get install clang-8

#to set up pyco its best to use virtualenv:
cd univar
virtualenv -p python3 cpython3
. cpython3/bin/activate
pip install -r requirements_pyco.txt 


#then you can run it like so:

#fish shell:
./pyin/tau2.py ./pyco_runner.sh tests/simple/*  2>&1 | tee  (date "+%F-%H-%M-%S") | grep ":test:"


#bash:
./pyin/tau2.py ./pyco_runner.sh tests/simple/*  2>&1 | tee  `date "+%F-%H-%M-%S"` | grep ":test:"


#pyco will output a trace, point your browser to the pyco_visualization directory and use left and right arrows to move around the trace steps


env PYTHONUNBUFFERED=1 ./pyin/tau2.py   "./pyco_runner.sh --novalgrind  true --nodebug true   --oneword true  --profile false   " tests/clean/zzpanla/ldl0     2>&1 | tee runs/(date "+%F-%H-%M-%S") | tee runs/last
