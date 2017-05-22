# Metadata for the composition of invertebrates in the litter bags at the end of the experiment 

## File

    bugs_2017.csv
    
## Description

* Collected by: KF 

* Collected on 22 March 2017

* Affiliation: Longwood University

* Location: Longwood University

## Modified

These data were collected as part of the litter habitat subsidy experiment conducted in the Spring of 2017. 

Details about the experimental set-up can be found in the [litter_habitat_subsidy lab_notebook](https://github.com/KennyPeanuts/litter_habitat_subsidy/blob/master/lab_notebook/habitat_setup_sp2017.md).

The data show the type and abundance of animals recovered from the leaf packs at the end of the experiment.

## Variable Descriptions

* site = the unique identifier for each specific leaf bag
    
* litter = the different types of litter in the leaf bags
    * COND = conditioned leaves collected from the pond - the leaves were primarily from willow oak, southern red oak, red maple, black-jack oak, and black gum.
    * BAG = leaf shapes cut from brown paper lunch bags
    * UC = unconditioned leaves collected from the forest floor adjacent to the pond - the leaves were primarily from willow oak, southern red oak, black-jack oak, northern red oak
   
* rep = the replicate of each litter type
    
* Ancl = the number of the limpets in the family Anclidae 
  
* Caen = the number of Ephmeroptera larvae in the family Caenidae
    
* Cerato = the number of Diptera larvae in the family Ceratopogonidae
    
* Chiro = the number of Diptera larvae in the family Chironimidae and tribe Chironominae
    
* Coen = the number of the Odonata larvae in the suborder Zygoptera and family Coenagrionidae
    
* Gyralus = the number of Gastropods of the species _Gyralus_ _deflectus_
    
* Hydrop = the number of Tricoptera larvae in the family Hydroptilidae
    
* Hydra = the number of Hydra
    
* Oligo = the number of oligochaete fragments in the sample.  NOTE = the oligochaetes were not likely sampled or quantified effectively
    
* Ortho = the number of Diptera larvae in the family Chironomidae and the tribe Orthocladinae
    
* Tany = the number of Diptera larvae in the family Chironomidae and the tribe Tanypodinae

## Data Entry

    site <- c("COND.B", "COND.A", "COND.C", "BAG.A", "BAG.B", "BAG.C", "UC.A", "UC.C", "UC.B")
    litter <- c("COND", "COND", "COND", "BAG", "BAG", "BAG", "UC", "UC", "UC")
    rep <- c("B", "A", "C", "A", "B", "C", "A", "C", "B")
    # Taxa
    Ancl <- c(1, 0, 0, 0, 0, 0, 1, 0, 0)
    Caen <- c(0, 4, 0, 3, 0, 0, 1, 0, 0) 
    Cerato <- c(0, 0, 0, 0, 0, 1, 1, 0, 0)
    Chiro <- c(10, 2, 6, 4, 0, 5, 7, 3, 9)
    Coen <- c(0, 0, 2, 0, 0, 0, 0, 1, 0)
    Gyralus <- c(1, 5, 12, 0, 0, 0, 1, 5, 3)
    Hydrop <- c(1, 0, 2, 0, 0, 1, 1, 0, 3)
    Hydra <- c(1, 0, 0, 0, 0, 0, 0, 0, 0)
    Oligo <- c(0, 0, 0, 0, 0, 9, 0, 1, 14)
    Ortho <- c(4, 4, 0, 4, 0, 0, 1, 5, 8)
    Tany <- c(0, 0, 0, 1, 0, 0, 0, 0, 0)
    
     
### Make Data Frame

    bugs <- data.frame(site, litter, rep, Ancl, Caen, Cerato, Chiro, Coen, Gyralus, Hydrop, Hydra, Oligo, Ortho, Tany)

### Create Matrix 
    
To create the matrix I removed the site designators and then converted it into a matrix.
    
The sites are in the same order as they were in the original data.frame
    
    bug.mat <- (as.matrix(bugs[, 4:14]))
    
## Write Table
### Data Frame
    
    write.table(bugs, "./data/bugs_2017.csv", row.names = F, quote = F, sep = ",")
    
### Matrix

    write.table(bug.mat, "./data/bugs_matrix_2017.csv", row.names = F, quote = F, sep = ",")
