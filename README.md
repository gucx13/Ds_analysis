# Ds_analysis

* data
	*Ap
	- ApUpcharm2013.root 
	  raw data.calculate the invariant mass of KKPI(t3),LcPKPi(t5).
	- ApDowncharm2013.root 
	  same as up.
	- CopyTree.C
	  selection about pseudorapidity and momentum cut && track cut && pid cut && Ds cut.
	- CalLogChi2.C
	  create a new branch IPCHI2.
	*pA
	 same as Ap
	*tuple_D2KKP_Lc2PKPi
	 DaVinci.py && JS_pAcharm.py are DaVinci script.

* MC(unfinished)
	*Geo_Ds
	 Produce GenDsMC.root for acceptance study.
	*Full_Ds
         *tuple_for_truth_matching
	  tuple for truth matching 
         *tuple
          tuple for other eff(SelEff)
* AccpEff
	-AddMCBtag.py 
	 use GenDsMC.root to add a new branch FROMB tag,produce GenDsMCBtag.root we only care prompt event.
	-GetEff.py
	 use y && pt divide bins and FROMB cut && GEO cut calculate Eff (the y is in pPa center frame).

* TruthMateff
	-CopyTree.C 
	 use /MC/Full_Ds/tuple_for_truth_matching/ tuples and the selections are same with the data.For matched candidate.
	-CopyTreeGhost.C 
	 same as CopyTree.C but for unmatched candidate.
	-FitMassGhost.C
	 Find how much signal in ghost, fit with CBS and poly.
	-FitMassMatch.C
	 find how much signal in ghost, fit with CBS and poly.
	-ana_matching.py
         without fit using sideband,divide bins for y && pT. It is nonsense because of the limitation of statistic.

* SelEff
	-CopyTree.C
	 use /MC/Full_Ds/tuple/ tuples to produce NoPIDCut.root with Truthmatch cut.
	-AddBtag.py
	 add 'FromB' tag to NoPIDCut.root, generate NoPIDCutBtag.root.
	-CalLogChi2.C
	 add LogIPchi2 to NoPIDCutBtag.root, generate NoPIDCutBtag_logipchi2.root
	-CopyTreeMC.C
	 copy out MCDecayTree from Full MC dst, generate MC.root
	-AddMCBtag.py
	 add 'FromB' tag to MC.root, generate MCBtag.root
	-GetEfforg.py
	 read in MC.root and NoPIDCutBtag_logipchi2.root, apply correction to single track efficiency 'ratio2012S20.root', get the reconstruction & selection efficiecy &&Scaled eff(nTrack,nVeloCluster,nTstationCluster), save to AllEff.root, note that the efficiency here doesn't consider the occupancy effect
	-GetEff.py
	 similar to GetEfforg.py, added some varialbes to determine some parameters used in RefEff
	-PrintEff.py
	 print out the sel eff to txt tables in ./Results/ for totEff/

* PIDEff
	-GetEff.py
	 define two func GetEffData(not use) && GetEffMC to calculate the Ap and pA PIDEff.

* FitMass
	-SeparateFile_Ap.C
         separate ApUpcharm2013_cut_logipchi2.root && ApDowncharm2013_cut_logipchi2.root bin by bin and save in data
	-SeparateFile_pA.C
	 same as SeparateFile_Ap.C
	-FitMass.C
	 run SeperateFile and fit in every y&pt bins : sig func is double gauss,bkg func is Chebychev.Save in fig.
	-FitMassCBS.C
 	 

* Question
	-why the truthmatch eff use diff tuple with the other eff?
	-why the truthmatch eff don't divide B&F y&pT?(statistic)

