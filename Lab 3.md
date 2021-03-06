# Lab Exercise 3

> 19.7/20

## Exercise Questions 1
1) 704 collections
2)  24429

1) Like all the other taxa in this collection, Rafinesquina alternata needs "ID"- proof of its existence
and validity. Conrad 1838 is the abbreviated citation of a reference that gives this species its bona fides.

> Not quite. Conrad 1838 was the first person to *name* the taxon. -0.5 points

2) Class: Strophomenata
   Order: Strophomenida
   Family: Strophomenidae
   Genus: Strophomena
   Species: planumbona

3) Union County

4) Late/Upper Ordovician

5) Liberty Formation

## Exercise Questions 2
1) The different colors represent occurences from different time periods.

2) The United States, the United Kingdom, and Belgium.

3) Cincinnati

4) Ordovician

## Section 2

1) Parallel

2) Myalinida

## Exercise Questions 3
1. https://training.paleobiodb.org/data1.2/occs/list.json?datainfo&rowcount&base_name=Ambonychia&strat=Lexington%20Limestone
2. https://training.paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Mammalia&interval=Paleocene,Oligocene
3. https://training.paleobiodb.org/data1.2/taxa/opinions.tsv?datainfo&rowcount&base_name=Testudines&interval=Triassic,Cretaceous
4. https://training.paleobiodb.org/data1.2/colls/list.csv?datainfo&rowcount&base_name=Aves, Marsupialia, Sirenia&cc=US
5. <strike>https://training.paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Ficus</strike>

> -1 points, you need to use Gastropoda:Ficus, to ensure you don't get the plant ficus

## Exercise Questions 4

1) Gastrocoptidae

2) Aptian Interval

3) Bridgerian Interval

4) Tropics

5) Kotodzha and Raiga Formations

## Exercise Questions 5

1) URL<-"https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Pliocene"
   Pliocene<-read.csv(URL)

2) 39 13

> Show the code next time

3) collections

4) Mammut, colloquial name: Mammoth. Data is limited to the Pliocene.

5) https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene

6) https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene&show=paleoloc

## Question 6
downloadPBDB<-function(taxon="TAXON",interval="INTERVAL"){
URL1<-"https://paleobiodb.org/data1.2/occs/list.csv?base_name="
URL2<-"&interval="
TaxonURL<-paste(URL1,taxon,URL2,interval,sep="")
Taxonreadout<-read.csv(TaxonURL)
Taxonreadout}

> Righteous!

## Morphologic Measurements
1) The following groupings are based entirely on shell diameter, the only characteristic shared by the PBDB
and the "Ammonites" dataset.

Glyptophiceras sinuatum:3,4,7,20,21
Xenoceltites variocostatus:2,5,6,12,16,17,18,23,24
Submeekoceras mushbachanum: 1,8,9,10,11,13,19,22,25

2) A. Brayard and H. Bucher. 2008. Smithian (Early Triassic) ammonoid faunas from northwestern 
Guangxi (South China): taxonomy and biochronology. Fossils and Strata 55:1-179

3) 2,5,6,12,16,17,18,23,24. In addition to being within the size groupings presented by the PBDB, these specimens
,like the plates from Brayard and Bucher, are small and have gentle ridges along the shell surface.  
