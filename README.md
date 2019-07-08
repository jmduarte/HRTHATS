# NanoHRTHATS
```bash
cmsrel CMSSW_10_2_15
cd CMSSW_10_2_15/src/ 
cmsenv
git cms-init
git cms-merge-topic cms-nanoAOD:master-102X 
git checkout -b nanoAOD cms-nanoAOD/master-102X 

git clone https://github.com/cms-nanoAOD/nanoAOD-tools.git PhysicsTools/NanoAODTools
git clone https://github.com/hqucms/NanoHRT PhysicsTools/NanoHRT
git clone https://github.com/hqucms/NanoHRT-tools.git PhysicsTools/NanoHRTTools

scram b -j 8

cmsDriver.py test_nanoHRT_mc -s NANO -n 1000 --mc --eventcontent NANOAODSIM --datatier NANOAODSIM --no_exec --conditions 102X_mcRun2_asymptotic_v7 --era Run2_2016,run2_nanoAOD_94X2016 --customise PhysicsTools/NanoHRT/nanoHRT_cff.nanoHRT_customizeMC --filein /store/mc/RunIISummer16MiniAODv2/BulkGravTohhTohbbhbb_narrow_M-2500_13TeV-madgraph/MINIAODSIM/PUMoriond17_80X_mcRun2_asymptotic_2016_TrancheIV_v6-v1/80000/A88400F5-39B6-E611-BEB3-A0369F7F9DE0.root --fileout file:nano_mc.root --customise_commands "process.options = cms.untracked.PSet(wantSummary = cms.untracked.bool(True)); process.add_(cms.Service('InitRootHandlers', EnableIMT = cms.untracked.bool(False)))"
```