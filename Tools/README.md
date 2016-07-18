diffNuisances.py
==================

Script used to check post-fit nuisances.


    Some documentation can be found here:
    https://twiki.cern.ch/twiki/bin/viewauth/CMS/HiggsWG/HiggsPAGPreapprovalChecks    

    
example:

    cd /afs/cern.ch/user/a/amassiro/Framework/Combine/CMSSW_7_4_7/src/LatinoCombineTools/Tools
    cmsenv
    cd /afs/cern.ch/user/a/amassiro/Framework/CMSSW_8_0_5/src/PlotsConfigurations/Configurations/
    combine -M MaxLikelihoodFit -t -1 --expectSignal 1  --rMin=-2 --rMax=4      superCombination.Total.txt.pruned.txt    >   result.MaxLikelihoodFit.superCombination.Total.txt.pruned.txt
    
    ... wait ...
    cd /afs/cern.ch/user/a/amassiro/Framework/Combine/CMSSW_7_4_7/src/LatinoCombineTools/Tools
    python diffNuisances.py -a /afs/cern.ch/user/a/amassiro/Framework/CMSSW_8_0_5/src/PlotsConfigurations/Configurations/mlfit.root -g plots.root.
    
    
