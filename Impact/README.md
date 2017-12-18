Impact plot without correlation
====


    - nominal fit (as previously)

    - scale up/down each nuisance and get the new signal strength freezing all the nuisances at their best value extracted from the "best fit"

    - the variation of the signal strength is used in the right part of the impact plot and is is used in the ranking



How to use:

    Impacts on Asimov MC

    combineTool.py -M Impacts -d workspace.my.root -m 125 --doInitialFit --robustFit 1  --expectSignal=1 -t -1    --saveWorkspace

    combineTool.py -M Impacts -d higgsCombine_initialFit_Test.MultiDimFit.mH125.root -m 125 --robustFit 1 --doFits --parallel 20  --expectSignal=1  -t -1    --job-mode lxbatch --task-name lxbatch-test --sub-opts='-q 1nd'   --snapshotName MultiDimFit  --doImpactNoCorr   

    combineTool.py -M Impacts -d higgsCombine_initialFit_Test.MultiDimFit.mH125.root -m 125  --expectSignal=1  -t -1  --doImpactNoCorr  -o workspace.my.root_impacts_datacard.MCAsimov.MYNEW.json

    plotImpacts.py -i workspace.my.root_impacts_datacard.MCAsimov.MYNEW.json  -o impacts_datacard_MCAsimov.MYNEW


Get back the standard impact plot:


    combineTool.py -M Impacts -d workspace.my.root -m 120 --robustFit 1 --doFits --parallel 20  --expectSignal=1  -t -1    --job-mode lxbatch --task-name lxbatch-test --sub-opts='-q 1nd'     

    combineTool.py -M Impacts -d workspace.my.root -m 120  --expectSignal=1  -t -1   -o workspace.my.root_impacts_datacard.MCAsimov.json

    plotImpacts.py -i workspace.my.root_impacts_datacard.MCAsimov.json  -o impacts_datacard_MCAsimov



    
