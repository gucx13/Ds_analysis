# Ds_analysis

* data
	*Ap
	- ApUpcharm2013.root 
	  raw data.calculate the invariant mass of KKPI(t3),LcPKPi(t5)
	- ApDowncharm2013.root 
	  same as up
	- CopyTree.C
	  selection about pseudorapidity and momentum cut && track cut && pid cut && Ds cut
	- CalLogChi2.C
	  create a new branch IPCHI2
	*pA
	 same as Ap
	*tuple_D2KKP_Lc2PKPi
	 DaVinci.py && JS_pAcharm.py are DaVinci script.

* MC
	*Geo_Ds
	 Produce GenDsMC.root for acceptance study

* AccpEff
	-AddMCBtag.py 
	 use GenDsMC.root to add a new branch FROMB tag, we only care prompt event
	-GetEff.py
	 use y && pt divide bins and FROMB cut && GEO cut calculate Eff (the y is in pPa center frame)

* TruthMateff
	-CopyTree.C 
	 use /MC/Full_Ds/tuple_for_truth_matching/
* Question

