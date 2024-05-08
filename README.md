## Installation
- ```cmsrel CMSSW_10_2_16_UL```
- ```cd CMSSW_10_2_16_UL/src```
- ```cmsenv```
- ```git clone git@github.com:cghuh/ttbarToBsToTauTau.git```
- ```python condor/setup.py```

After running the setup.py, the filelists are automatically generated using condor/filelist_2018.txt

### Run code locally
- ```source setup.sh```
- ```make -j6 Analyzer Plotter```
- ```./Analzer test.root filelists/2018/backgrounds/TTToSemiLeptonic_TuneCP5_13TeV-powheg-pythia8.txt year=2018```
additional option: ```ilast=NEVENT```, ```debug=True``` (default is False)


### Run using condor (Basically performed with CMS connect)
- ```python condor/run_all.py --full --plot --batch --condor --run --outdir=results/run_2024_03_27 --optim --nevt=300000```
- It create histogram ROOT file ```results/run_2024_03_27.root```
- From histogram ROOT file, plotting results are stored in ```results/Plotter_out_2024_03_27.root```
- Suggest to run on ```screen```


## Explanation of code
- ```Analyzer.cc```: main code
- ```settings.h```: Set option (systematic on/off, scale factor on/off)
- ```include/Variables.h```: Define object and event variables
- ```include/Weighting.h```: Apply weighting(Trigger, L1Prefiring, Pileup, top pT, ...)
- ```EventSelections.h```: Define signal or control regions
- ```include/ScaleFactors.h```: Calculate scale factors for each event and apply them to each region
- ```include/PlottingBase.h```: Define and fill histograms