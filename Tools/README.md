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
    python diffNuisances.py -a /afs/cern.ch/user/a/amassiro/Framework/CMSSW_8_0_5/src/PlotsConfigurations/Configurations/mlfit.root -g plots.root
    
    

New features:

    It produces pdf file similar to the impact plot style.
    It allows to give the list of nuisances to draw: from the standard impact plot we get the list of nuisances to be drawn, and we draw only those
    
    example:
    
    python diffNuisances.py -a /afs/cern.ch/user/a/amassiro/Framework/CMSSW_8_0_5/src/PlotsConfigurations/Configurations/mlfitCombined.vbf.pruned.txt.MaxLikelihoodFit.0.5.root.root    -g plots.root   -o testdpf.root  -i example/listNuisances.json

Comparison between two fits:

    The parameters of two fits can be compared with a dedicated script. The order of the nuisances must be specified via a txt file.
    
    Example:
     
    python diffNuisances_compare.py -A fitDiagnostics.A.root  -B fitDiagnostics.B.root -o output.pdf --order ordered_nuisances.txt

    e.g. Data-Asimov vs Data

# PRODUCE PULLS

    cd <yourDirectory>/CMSSW_7_4_7/src/HiggsAnalysis/CombinedLimit/

    cmsenv 

    cd -

For background-only Asimov dataset:

    combine -M MaxLikelihoodFit -t -1 --expectSignal 0 --robustFit 1 --saveShapes --saveWithUncertainties datacard.txt -n myBkgAsimov

    python diffNuisances.py -a mlfitmyBkgAsimov.root -a -f latex --histogram pullsmyBkgAsimov.root

For signal + background Asimov dataset:

    combine -M MaxLikelihoodFit -t -1 --expectSignal 1 --robustFit 1 --saveShapes --saveWithUncertainties datacard.txt -n mySigAsimov

    python diffNuisances.py -a mlfitmySigAsimov.root -a -f latex --histogram pullsmySigAsimov.root

For real data:

    combine -M MaxLikelihoodFit --robustFit 1 --saveShapes --saveWithUncertainties datacard.txt -n myUnblind

    python diffNuisances.py -a mlfitmymyUnblind.root -a -f latex --histogram pullsmyUnblind.root







