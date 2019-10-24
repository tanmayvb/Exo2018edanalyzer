<p><b> The aim is to make all setup 2016, 2017 and 2018 in a same place. Currently devoliping for 2018 Data, MC </b></p>

Installation of ExoPieElement and dependencies for 2018 Data and Mc

##Working on lxplus7

##setup CMSSW 

##SCRAM ARCH SET for CMSSW_10_2_10

export SCRAM_ARCH=slc7_amd64_gcc700

cmsrel CMSSW_10_2_17

cd CMSSW_10_2_17/src/

git cms-initgit cms-merge-topic cms-egamma:EgammaPostRecoTools

git cms-merge-topic cms-met:METFixEE2017_949_v2_backport_to_102X ##Twiki: https://twiki.cern.ch/twiki/bin/view/CMS/MissingETUncertaintyPrescription

git clone git@github.com:ExoPie/ExoPieElement.git

scram b -j 4

git clone git@github.com:cms-jet/JetToolbox.git JMEAnalysis/JetToolbox
git checkout jetToolbox_94X_v3

## Should change with this need to check : git checkout  jetToolbox_102X_v2
scram b -j 4

cd ExoPieElement/TreeMaker/test/

## For Photon ID and other
Please change treeMaker_Summer17_cfg.py by the followings:

1--> from RecoEgamma.EgammaTools.EgammaPostRecoTools import setupEgammaPostRecoSeq
setupEgammaPostRecoSeq(process,era='2018-Prompt')    ## Twiki: https://twiki.cern.ch/twiki/bin/view/CMS/EgammaPostRecoRecipes#Running_on_2017_MiniAOD_V2

2-->Global tag 94X_mc2017_realistic_v12 to 100X_upgrade2018_realistic_v10 for botha Data and MC ## Twiki: https://twiki.cern.ch/twiki/bin/view/CMSPublic/SWGuideFrontierConditions

3--> Input file name by "/store/mc/RunIIAutumn18MiniAOD/QCD_Pt_600to800_TuneCP5_13TeV_pythia8/MINIAODSIM/102X_upgrade2018_realistic_v15-v1/80000/FC11B45B-C0E0-0F4B-8A04-E216B0A7C320.root" 

Then run the test file by

cmsRun treeMaker_Summer17_cfg.py
