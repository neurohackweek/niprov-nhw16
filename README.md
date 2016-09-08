# Niprov
> Neurohackweek 2016

> Jasper J.F. van den Bosch

*Slides at neurohackweek.github.com/niprov-nhw16*

#### Setup python environment
```shell
virtualenv env
source env/bin/activate
pip install -U pip
```

#### Download sample data
```shell
wget https://github.com/ilogue/niprov/archive/master.zip
unzip master.zip
cd niprov-master
```

#### Install Niprov
```shell
pip install niprov
```

#### Optional packages
```shell
pip install -r optional.txt # pydicom nibabel mne matplotlib
```

#### Why niprov?

* reproducibility
* need story, metadata of brain images
* provenance: history, origin of a file
* **N**euro**I**maging **Prov**enance
 

#### Commandline API

```shell
provenance -h
provenance discover ./testdata
provenance export
provenance export --file testdata/parrec/T1.PAR
provenance record "parrec2nii testdata/parrec/T1.PAR" --parent testdata/parrec/T1.PAR --new T1.nii
provenance record "mcflirt -in T1.nii -out T1_reg.nii.gz"
provenance export --file T1_reg.nii.gz
```

#### Web browser
```shell
provenance serve
```

#### Python API
```python
from niprov import ProvenanceContext
provenance = ProvenanceContext()

for image in provenance.get().bySubject('05aug14test'):
    image.viewSnapshot() 

# Make sure two files were acquired with the same parameters:
img1.compare(img2).assertEqual()
```

#### Configuration
```shell
cp niprov.cfg ~/niprov.cfg
gedit ~/niprov.cfg
```






