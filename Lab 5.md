## Lab 5

> Good Job, 18/20

````R
source("https://raw.githubusercontent.com/aazaff/paleobiologyDatabase.R/master/communityMatrix.R")
source("https://raw.githubusercontent.com/aazaff/paleobiologyDatabase.R/master/cullMatrix.R")
DataPBDB<-downloadPBDB(Taxa=c("Bivalvia","Brachiopoda"),StartInterval="Ordovician",StopInterval="Pleistocene")
DataPBDB<-cleanGenus(DataPBDB)
Epochs<-downloadTime(Timescale="international epochs")
DataPBDB<-constrainAges(DataPBDB,Epochs)
Brachiopods<-DataPBDB[which(DataPBDB[,"phylum"]=="Brachiopoda"),]
Bivalves<-DataPBDB[which(DataPBDB[,"class"]=="Bivalvia"),]
BrachiopodAbundance<-abundanceMatrix(Brachiopods,SampleDefinition="early_interval")
BivalveAbundance<-abundanceMatrix(Bivalves,SampleDefinition="early_interval")
````

## Problem Set 1

1) #First, we isolate the Miocene bivalves. Then, we find how many genera have abundances greater than 0.

````R
Bivalves1<-BivalveAbundance["Miocene",]
Bivalves2<-which(Bivalves1>0)
length(Bivalves2)
[1] 634
````

2) #First, we find the abundance of the dominant species. Then, we find the total abundance of every bivalve.

````R
Bivalves1<-BivalveAbundance["Pliocene",]
Bivalves2<-which(Bivalves1>0)
max(Bivalves2)
[1] 2266
sum(Bivalves2)
[1] 562450
2266/562450
[1] 0.004028803
````

> -1 Points. I belive where you went wrong was at Bivalves2<-which(Bivalves1>0) you needed Bivalves1[which(Bivalves1>0)]

3)
````R
Brachiopods1<-BrachiopodAbundance["Late Ordovician",]
Brachiopods2<-Brachiopods1[which(Brachiopods1>0)]
sum(Brachiopods2)
[1] 6154

1-sum((Brachiopods2/6154)^2)
[1] 0.9784588
````

4)
```R
Bivalves1<-BivalveAbundance["Late Cretaceous",]
Bivalves2<-Bivalves1[which(Bivalves1>0)]
sum(Bivalves2)
[1] 29684
-sum((Bivalves2/29684)*(log(Bivalves2/29684)))
[1] 5.086654
````

5)
````R
Bivalves1<-BivalveAbundance["Paleocene",]
Bivalves2<-Bivalves1[which(Bivalves1>0)]
sum(Bivalves2)
[1] 4238
-sum((Bivalves2/4238)*(log(Bivalves2/4238)))
[1] 4.511875
````

6)
````R
[1] 4.511875/5.08665
[1] 0.8870025
#Shannon's entropy decreased by about 12%. The K/T extinction might explain the changes in diversity. 
````

7)

````R
 exp(4.511875)
[1] 91.09246
exp(5.08665)
[1] 161.8468
91.09246/161.8468
[1] 0.5628314
#Diversity instead decreases by about 44%. This may well be a more accurate representation of the K/T
#extinction in which many species disappeared.
````

# Problem Set 2
````R
library(vegan)
?diversity
````

1)

````R
MioceneBivalves<-BivalveAbundance["Miocene",]
specnumber(MioceneBivalves, MARGIN=1)
[1] 634
````

2)
````R
LateOrdovicianBrachiopods<-BrachiopodAbundance["Late Ordovician",]
diversity(LateOrdovicianBrachiopods,index="simpson")
[1] 0.9784588
````

3)
````R
CretaceousBivalves<-BivalveAbundance["Late Cretaceous",]
diversity(CretaceousBivalves,index="shannon")
[1] 5.086654
````

4)
````R
PaleoceneBivalves<-BivalveAbundance["Paleocene",]
diversity(PaleoceneBivalves,index="shannon")
[1] 4.511875
````

## Problem Set 3 

1)
> You aren't kidding!

````R
#This is a lot of text.
MississippianBrachiopods<-BrachiopodAbundance["Mississippian",]    
PennsylvanianBrachiopods<-BrachiopodAbundance["Pennsylvanian",]  
EarlyOrdovicianBrachiopods<-BrachiopodAbundance["Early Ordovician",] 
MiddleOrdovicianBrachiopods<-BrachiopodAbundance["Middle Ordovician",]                                                                
LateOrdovicianBrachiopods<-BrachiopodAbundance["Late Ordovician",]        
LlandoveryBrachiopods<-BrachiopodAbundance["Llandovery",]
WenlockBrachiopods<-BrachiopodAbundance["Wenlock",]   
LudlowBrachiopods<-BrachiopodAbundance["Ludlow",]                                                    
PridoliBrachiopods<-BrachiopodAbundance["Pridoli",]   
EarlyDevonianBrachiopods<-BrachiopodAbundance["Early Devonian",] 
MiddleDevonianBrachiopods<-BrachiopodAbundance["Middle Devonian",]  
LateDevonianBrachiopods<-BrachiopodAbundance["Late Devonian",]                                             
CisuralianBrachiopods<-BrachiopodAbundance["Cisuralian",]  
LateJurassicBrachiopods<-BrachiopodAbundance["Late Jurassic",]      
EoceneBrachiopods<-BrachiopodAbundance["Eocene",] 
LateCretaceousBrachiopods<-BrachiopodAbundance["Late Cretaceous",]                                                               
EarlyCretaceousBrachiopods<-BrachiopodAbundance["Early Cretaceous",]  
MiddleJurassicBrachiopods<-BrachiopodAbundance["Middle Jurassic",]     
PaleoceneBrachiopods<-BrachiopodAbundance["Paleocene",]       
LopingianBrachiopods<-BrachiopodAbundance["Lopingian",]                                                      
EarlyJurassicBrachiopods<-BrachiopodAbundance["Early Jurassic",]    
GuadalupianBrachiopods<-BrachiopodAbundance["Guadalupian",] 
MiddleTriassicBrachiopods<-BrachiopodAbundance["Middle Triassic",]  
LateTriassicBrachiopods<-BrachiopodAbundance["Late Triassic",]                                                    
MioceneBrachiopods<-BrachiopodAbundance["Miocene",] 
EarlyTriassicBrachiopods<-BrachiopodAbundance["Early Triassic",]       
PlioceneBrachiopods<-BrachiopodAbundance["Pliocene",]     
PleistoceneBrachiopods<-BrachiopodAbundance["Pleistocene",] 
OligoceneBrachiopods<-BrachiopodAbundance["Oligocene",]
MississippianBivalves<-BivalveAbundance["Mississippian",]    
PennsylvanianBivalves<-BivalveAbundance["Pennsylvanian",]  
EarlyOrdovicianBivalves<-BivalveAbundance["Early Ordovician",] 
MiddleOrdovicianBivalves<-BivalveAbundance["Middle Ordovician",]                                                                   
LateOrdovicianBivalves<-BivalveAbundance["Late Ordovician",]        
LlandoveryBivalves<-BivalveAbundance["Llandovery",]
WenlockBivalves<-BivalveAbundance["Wenlock",]   
LudlowBivalves<-BivalveAbundance["Ludlow",]                                                    
PridoliBivalves<-BivalveAbundance["Pridoli",]   
EarlyDevonianBivalves<-BivalveAbundance["Early Devonian",] 
MiddleDevonianBivalves<-BivalveAbundance["Middle Devonian",]  
LateDevonianBivalves<-BivalveAbundance["Late Devonian",]                                             
CisuralianBivalves<-BivalveAbundance["Cisuralian",]  
LateJurassicBivalves<-BivalveAbundance["Late Jurassic",]      
EoceneBivalves<-BivalveAbundance["Eocene",] 
LateCretaceousBivalves<-BivalveAbundance["Late Cretaceous",]                                                               
EarlyCretaceousBivalves<-BivalveAbundance["Early Cretaceous",]  
MiddleJurassicBivalves<-BivalveAbundance["Middle Jurassic",]     
PaleoceneBivalves<-BivalveAbundance["Paleocene",]       
LopingianBivalves<-BivalveAbundance["Lopingian",]                                                      
EarlyJurassicBivalves<-BivalveAbundance["Early Jurassic",]    
GuadalupianBivalves<-BivalveAbundance["Guadalupian",] 
MiddleTriassicBivalves<-BivalveAbundance["Middle Triassic",]  
LateTriassicBivalves<-BivalveAbundance["Late Triassic",]                                                    
MioceneBivalves<-BivalveAbundance["Miocene",] 
EarlyTriassicBivalves<-BivalveAbundance["Early Triassic",]       
PlioceneBivalves<-BivalveAbundance["Pliocene",]     
PleistoceneBivalves<-BivalveAbundance["Pleistocene",] 
OligoceneBivalves<-BivalveAbundance["Oligocene",]                
specnumber(MississippianBrachiopods, MARGIN=1)
specnumber(PennsylvanianBrachiopods, MARGIN=1)
specnumber(EarlyOrdovicianBrachiopods, MARGIN=1)
specnumber(MiddleOrdovicianBrachiopods, MARGIN=1)                                                                
specnumber(LateOrdovicianBrachiopods, MARGIN=1)       
specnumber(LlandoveryBrachiopods, MARGIN=1)
specnumber(WenlockBrachiopods, MARGIN=1)
specnumber(LudlowBrachiopods, MARGIN=1)                                              
specnumber(PridoliBrachiopods, MARGIN=1)
specnumber(EarlyDevonianBrachiopods, MARGIN=1)
specnumber(MiddleDevonianBrachiopods, MARGIN=1)
specnumber(LateDevonianBrachiopods, MARGIN=1)                                            
specnumber(CisuralianBrachiopods, MARGIN=1) 
specnumber(LateJurassicBrachiopods, MARGIN=1) 
specnumber(EoceneBrachiopods, MARGIN=1)
specnumber(LateCretaceousBrachiopods, MARGIN=1)                                                            
specnumber(EarlyCretaceousBrachiopods, MARGIN=1) 
specnumber(MiddleJurassicBrachiopods, MARGIN=1)   
specnumber(PaleoceneBrachiopods, MARGIN=1)     
specnumber(LopingianBrachiopods, MARGIN=1)                                                
specnumber(EarlyJurassicBrachiopods, MARGIN=1) 
specnumber(GuadalupianBrachiopods, MARGIN=1)
specnumber(MiddleTriassicBrachiopods, MARGIN=1)
specnumber(LateTriassicBrachiopods, MARGIN=1)                                                
specnumber(MioceneBrachiopods, MARGIN=1)
specnumber(EarlyTriassicBrachiopods, MARGIN=1)       
specnumber(PlioceneBrachiopods, MARGIN=1)
specnumber(PleistoceneBrachiopods, MARGIN=1)
specnumber(OligoceneBrachiopods, MARGIN=1) 
specnumber(MississippianBivalves, MARGIN=1)     
specnumber(PennsylvanianBivalves, MARGIN=1)  
specnumber(EarlyOrdovicianBivalves, MARGIN=1)  
specnumber(MiddleOrdovicianBivalves, MARGIN=1)                                                                   
specnumber(LateOrdovicianBivalves, MARGIN=1)         
specnumber(LlandoveryBivalves, MARGIN=1) 
specnumber(WenlockBivalves, MARGIN=1)    
specnumber(LudlowBivalves, MARGIN=1)                                                    
specnumber(PridoliBivalves, MARGIN=1)    
specnumber(EarlyDevonianBivalves, MARGIN=1)  
specnumber(MiddleDevonianBivalves, MARGIN=1)   
specnumber(LateDevonianBivalves, MARGIN=1)                                              
specnumber(CisuralianBivalves, MARGIN=1)   
specnumber(LateJurassicBivalves, MARGIN=1)      
specnumber(EoceneBivalves, MARGIN=1) 
specnumber(LateCretaceousBivalves, MARGIN=1)                                                             
specnumber(EarlyCretaceousBivalves, MARGIN=1)   
specnumber(MiddleJurassicBivalves, MARGIN=1)    
specnumber(PaleoceneBivalves, MARGIN=1)        
specnumber(LopingianBivalves, MARGIN=1)                                                      
specnumber(EarlyJurassicBivalves, MARGIN=1)     
specnumber(GuadalupianBivalves, MARGIN=1) 
specnumber(MiddleTriassicBivalves, MARGIN=1)   
specnumber(LateTriassicBivalves, MARGIN=1)                                                  
specnumber(MioceneBivalves, MARGIN=1) 
specnumber(EarlyTriassicBivalves, MARGIN=1)       
specnumber(PlioceneBivalves, MARGIN=1)   
specnumber(PleistoceneBivalves, MARGIN=1) 
specnumber(OligoceneBivalves, MARGIN=1)    
````

> That works! Consider the ````apply( )```` function next time... much easier.

Brachiopods
Mississippian 314
Pennsylvanian 284
EarlyOrdovician 141
MiddleOrdovician 282
LateOrdovician 331                                                           
Llandovery 271
Wenlock 257
Ludlow 234
Pridoli 138
EarlyDevonian 497
MiddleDevonian 353
LateDevonian 274
Cisuralian 564
LateJurassic 111
Eocene 57
LateCretaceous 96
EarlyCretaceous 125
MiddleJurassic 175
Paleocene 29
Lopingian 406
EarlyJurassic 130
Guadalupian 549
MiddleTriassic 111
LateTriassic 193
Miocene 45
EarlyTriassic 63
Pliocene 23
Pleistocene 19
Oligocene 30

````R
EpochBrachiopods<-array(c(314,284,141,282,331,271,257,234,138,497,353,274,564,111,57,96,125,175,29,406,130,549,
111,193,45,63,23,19,30),dimnames=list(c("Mississippian","Pennsylvanian","EarlyOrdovician","MiddleOrdovician",
"LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli","EarlyDevonian","MiddleDevonian","LateDevonian",
"Cisuralian","LateJurassic","Eocene","LateCretaceous","EarlyCretaceous","MiddleJurassic","Paleocene","Lopingian",
"EarlyJurassic","Guadalupian","MiddleTriassic","LateTriassic","Miocene","EarlyTriassic","Pliocene",
"Pleistocene","Oligocene")))
````

Bivalves
Mississippian 99
Pennsylvanian 104
EarlyOrdovician 42
MiddleOrdovician 48
LateOrdovician 87
Llandovery 56
Wenlock 66
Ludlow 81
Pridoli 51
EarlyDevonian 111
MiddleDevonian 88
LateDevonian 70
Cisuralian 160
LateJurassic 270
Eocene 512
LateCretaceous 574
EarlyCretaceous 393
MiddleJurassic 202
Paleocene 305
Lopingian 156
EarlyJurassic 217
Guadalupian 191
MiddleTriassic 151
LateTriassic 242
MioceneBivalves 634
EarlyTriassic 101
Pliocene 534
Pleistocene 498
Oligocene 355

````R
EpochBivalves<-array(c(99,104,42,48,87,56,66,81,51,111,88,70,160,270,512,574,393,202,305,156,217,191,151,242,634,
101,534,498,355),dimnames=list(c("Mississippian","Pennsylvanian","EarlyOrdovician","MiddleOrdovician",
"LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli","EarlyDevonian","MiddleDevonian","LateDevonian",
"Cisuralian","LateJurassic","Eocene","LateCretaceous","EarlyCretaceous","MiddleJurassic","Paleocene","Lopingian",
"EarlyJurassic","Guadalupian","MiddleTriassic","LateTriassic","Miocene","EarlyTriassic","Pliocene",
"Pleistocene","Oligocene")))

Epochs in order: ("EarlyOrdovician","MiddleOrdovician","LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli",
"EarlyDevonian","MiddleDevonian","LateDevonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","EarlyTriassic","MiddleTriassic","LateTriassic","EarlyJurassic","MiddleJurassic","LateJurassic",
"EarlyCretaceous","LateCretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")

EpochBrachiopods<-EpochBrachiopods[c("EarlyOrdovician","MiddleOrdovician","LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli",
"EarlyDevonian","MiddleDevonian","LateDevonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","EarlyTriassic","MiddleTriassic","LateTriassic","EarlyJurassic","MiddleJurassic","LateJurassic",
"EarlyCretaceous","LateCretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")]

EpochBivalves<-EpochBivalves[c("EarlyOrdovician","MiddleOrdovician","LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli",
"EarlyDevonian","MiddleDevonian","LateDevonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","EarlyTriassic","MiddleTriassic","LateTriassic","EarlyJurassic","MiddleJurassic","LateJurassic",
"EarlyCretaceous","LateCretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")]


cor(EpochBivalves,EpochBrachiopods)
[1] -0.567194
#Brachiopod richness is negatively correlated with bivalve richness.
````

2)

````R
SimpsonBrachiopods<-array(c(
(diversity(MississippianBrachiopods,index="shannon")), 
(diversity(PennsylvanianBrachiopods,index="shannon")),
(diversity(EarlyOrdovicianBrachiopods,index="shannon")),
(diversity(MiddleOrdovicianBrachiopods,index="shannon")),                                                               
(diversity(LateOrdovicianBrachiopods,index="shannon")),      
(diversity(LlandoveryBrachiopods,index="shannon")), 
(diversity(WenlockBrachiopods,index="shannon")), 
(diversity(LudlowBrachiopods,index="shannon")),                                           
(diversity(PridoliBrachiopods,index="shannon")), 
(diversity(EarlyDevonianBrachiopods,index="shannon")), 
(diversity(MiddleDevonianBrachiopods,index="shannon")), 
(diversity(LateDevonianBrachiopods,index="shannon")),                                       
(diversity(CisuralianBrachiopods,index="shannon")),
(diversity(LateJurassicBrachiopods,index="shannon")),
(diversity(EoceneBrachiopods,index="shannon")), 
(diversity(LateCretaceousBrachiopods,index="shannon")),                                                        
(diversity(EarlyCretaceousBrachiopods,index="shannon")),
(diversity(MiddleJurassicBrachiopods,index="shannon")), 
(diversity(PaleoceneBrachiopods,index="shannon")),    
(diversity(LopingianBrachiopods,index="shannon")),                                              
(diversity(EarlyJurassicBrachiopods,index="shannon")),
(diversity(GuadalupianBrachiopods,index="shannon")),
(diversity(MiddleTriassicBrachiopods,index="shannon")),
(diversity(LateTriassicBrachiopods,index="shannon")),                                              
(diversity(MioceneBrachiopods,index="shannon")),
(diversity(EarlyTriassicBrachiopods,index="shannon")),      
(diversity(PlioceneBrachiopods,index="shannon")),
(diversity(PleistoceneBrachiopods,index="shannon")),
(diversity(OligoceneBrachiopods,index="shannon"))))

SimpsonBivalves<-array(c(
(diversity(MississippianBivalves,index="shannon")),     
(diversity(PennsylvanianBivalves,index="shannon")),  
(diversity(EarlyOrdovicianBivalves,index="shannon")),  
(diversity(MiddleOrdovicianBivalves,index="shannon")),                                                                    
(diversity(LateOrdovicianBivalves,index="shannon")),        
(diversity(LlandoveryBivalves,index="shannon")),  
(diversity(WenlockBivalves,index="shannon")),    
(diversity(LudlowBivalves,index="shannon")),                                                     
(diversity(PridoliBivalves,index="shannon")),    
(diversity(EarlyDevonianBivalves,index="shannon")), 
(diversity(MiddleDevonianBivalves,index="shannon")),    
(diversity(LateDevonianBivalves,index="shannon")),                                               
(diversity(CisuralianBivalves,index="shannon")),   
(diversity(LateJurassicBivalves,index="shannon")),      
(diversity(EoceneBivalves,index="shannon")),
(diversity(LateCretaceousBivalves,index="shannon")),                                                            
(diversity(EarlyCretaceousBivalves,index="shannon")),   
(diversity(MiddleJurassicBivalves,index="shannon")),     
(diversity(PaleoceneBivalves,index="shannon")),         
(diversity(LopingianBivalves,index="shannon")),                                                      
(diversity(EarlyJurassicBivalves,index="shannon")),     
(diversity(GuadalupianBivalves,index="shannon")), 
(diversity(MiddleTriassicBivalves,index="shannon")),    
(diversity(LateTriassicBivalves,index="shannon")),                                                 
(diversity(MioceneBivalves,index="shannon")), 
(diversity(EarlyTriassicBivalves,index="shannon")),    
(diversity(PlioceneBivalves,index="shannon")),   
(diversity(PleistoceneBivalves,index="shannon")), 
(diversity(OligoceneBivalves,index="shannon"))))

GiniEpochBrachiopods<-array(c( 4.618776, 4.096848, 4.200277, 4.859976, 4.664635, 4.535380, 4.658886, 4.664010,
 4.325749, 5.296419, 4.546489, 4.398376, 5.353992, 3.927540, 3.338419, 3.517404,
 4.085487, 4.164713, 2.500670, 4.734245, 3.729191, 5.325329, 3.824816, 4.185167,
 3.216753, 3.125604, 2.611886, 2.573816, 3.106048),dimnames=list(c("Mississippian","Pennsylvanian","EarlyOrdovician","MiddleOrdovician",
"LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli","EarlyDevonian","MiddleDevonian","LateDevonian",
"Cisuralian","LateJurassic","Eocene","LateCretaceous","EarlyCretaceous","MiddleJurassic","Paleocene","Lopingian",
"EarlyJurassic","Guadalupian","MiddleTriassic","LateTriassic","Miocene","EarlyTriassic","Pliocene",
"Pleistocene","Oligocene")))

GiniEpochBivalves<-array(c( 3.844638, 3.755572, 3.357938, 3.227148, 3.560792, 3.148909, 3.628257, 3.567614,
 3.294253, 3.988784, 3.397504, 3.149485, 4.259922, 4.571792, 4.922578, 5.086654,
 4.894056, 4.410415, 4.511875, 4.160419, 4.299667, 4.454766, 4.127591, 4.516975,
 5.374768, 2.905877, 5.334865, 5.267982, 4.972140),dimnames=list(c("Mississippian","Pennsylvanian","EarlyOrdovician","MiddleOrdovician",
"LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli","EarlyDevonian","MiddleDevonian","LateDevonian",
"Cisuralian","LateJurassic","Eocene","LateCretaceous","EarlyCretaceous","MiddleJurassic","Paleocene","Lopingian",
"EarlyJurassic","Guadalupian","MiddleTriassic","LateTriassic","Miocene","EarlyTriassic","Pliocene",
"Pleistocene","Oligocene")))

GiniEpochBrachiopods<-GiniEpochBrachiopods[c("EarlyOrdovician","MiddleOrdovician","LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli",
"EarlyDevonian","MiddleDevonian","LateDevonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","EarlyTriassic","MiddleTriassic","LateTriassic","EarlyJurassic","MiddleJurassic","LateJurassic",
"EarlyCretaceous","LateCretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")]

GiniEpochBivalves<-GiniEpochBivalves[c("EarlyOrdovician","MiddleOrdovician","LateOrdovician","Llandovery","Wenlock","Ludlow","Pridoli",
"EarlyDevonian","MiddleDevonian","LateDevonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","EarlyTriassic","MiddleTriassic","LateTriassic","EarlyJurassic","MiddleJurassic","LateJurassic",
"EarlyCretaceous","LateCretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")]
    
cor(GiniEpochBivalves,GiniEpochBrachiopods)
[1] -0.5308717
#Brachiopod biodiversity is negatively correlated with bivalve diversity.
````

> You took a wrong turn somewhere... the correct answer is -0.23 The following is a correct version. -1 Points

````R
BivalveDiversity<-diversity(BivalveAbundance,"simpson")
BrachiopodDiversity<-diversity(BrachiopodAbundance,"simpson")
BivalveDiversity<-BivalveDiversity[names(BrachiopodDiversity)]
cor(BivalveDiversity,BrachiopodDiversity)
[1] -0.2355505
````

3)
EpochBrachiopods
#The Lopingian/Early Triassic barrier is the greatest drop in brachiopod richness.


## Problem Set 4
````R
subsampleIndividuals<-function(Abundance,Quota,Trials=100) {
      Richness<-vector("numeric",length=Trials)
      Abundance<-Abundance[Abundance>0]
      Pool<-rep(1:length(Abundance),times=Abundance)
      if (sum(Abundance) < Quota) {
            print("Fewer Individuals than Quota")
            return(length(unique(Pool)))
            }
      for (i in 1:Trials) {
            Subsample<-sample(Pool,Quota,replace=FALSE)
            Richness[i]<-length(unique(Subsample))
            }
      return(mean(Richness))
      }

SampleAbundances<-apply(BivalveAbundance,1,sum)
SampleAbundances[which(SampleAbundances==min(SampleAbundances))]
Early Ordovician 
	    124
StandardizedRichness<-apply(BivalveAbundance,1,subsampleIndividuals,Quota=124)
````

1) 
````R
BrachiopodAbundances<-apply(BrachiopodAbundance,1,sum)
BrachiopodAbundances[which(BrachiopodAbundances==min(BrachiopodAbundances))]
Pleistocene 
         63 
````

2)
````R
BrachiopodAbundances<-apply(BrachiopodAbundance,1,subsampleIndividuals,Quota=63)
StandardBrachiopods<-BrachiopodAbundances[c("Early Ordovician","Middle Ordovician","Late Ordovician","Llandovery","Wenlock","Ludlow","Pridoli",
"Early Devonian","Middle Devonian","Late Devonian","Mississippian","Pennsylvanian","Cisuralian","Guadalupian",
"Lopingian","Early Triassic","Middle Triassic","Late Triassic","Early Jurassic","Middle Jurassic","Late Jurassic",
"Early Cretaceous","Late Cretaceous","Paleocene","Eocene","Oligocene","Miocene","Pliocene","Pleistocene")]

cor(EpochBrachiopods,StandardBrachiopods)
[1] 0.8855588
#The unstandardized and standardized richnesses differ by about 11%. Standardization, then, has had a significant
#but not overwhelming effect on the quality of our data. 
````

3)

````R
plot(x=EpochBrachiopods,y=EpochBivalves)
plot(x=StandardBrachiopods, y=StandardizedRichness)
#Both plots display wide-ranging data values, which could obscure precise relationships. However, they both exhibit
#a general negative trend: when there are a lot of bivalves, there are not many brachiopods, and vice versa. 
#With this information, we might safely conclude that the two taxa were in competition with one another. The 
#degree to which the trend is evident depends on which graph one looks at; the standardized graph shows a somewhat
#murkier relationship than the unstandardized graph. In this case, viewing only the unstandardized data might give
#give one false confidence in the relationship between brachiopods and bivalves, and so I come to the conclusion that
#standardizing does indeed matter.
````

4)

````R
plot(EpochBrachiopods)
plot(EpochBivalves)
plot(StandardizedRichness)
plot(StandardBrachiopods)
#Viewing these plots, it seems clear that brachiopods decline while bivalves ascend. At face value, this could be
#seen as evidence that brachiopods were outcompeted by bivalves. However, this is not direct evidence that 
#competition is the culprit. After all, one could view the richnesses of dinosaurs and mammals across the 
#Cretaceous and Paleocene and conclude that our ancestors outcompeted Tyrannosaurus. Obviously, conclusions are
#premature. Nevertheless, there is some evidence in these analyses to support the theory of bivalves outcompeting
#brachiopods.
````
