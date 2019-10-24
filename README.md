# Exo2018edanalyzer
Installation of ExoPieElement and dependencies for 2018 Data and Mc
Working on lxplus7
setup CMSSW 
###SCRAM ARCH SET for CMSSW_10_2_10
export SCRAM_ARCH=slc7_amd64_gcc700
cmsrel CMSSW_10_2_17
cd CMSSW_10_2_17/src/
git cms-initgit cms-merge-topic cms-egamma:EgammaPostRecoTools
git cms-merge-topic cms-met:METFixEE2017_949_v2_backport_to_102X

git clone git@github.com:ExoPie/ExoPieElement.git

scram b -j 4

git clone git@github.com:cms-jet/JetToolbox.git JMEAnalysis/JetToolbox
git checkout jetToolbox_94X_v3

## Should change with this need to check : git checkout  jetToolbox_102X_v2
scram b -j 4

cd ExoPieElement/TreeMaker/test/
cmsRun treeMaker_Summer17_cfg.py
