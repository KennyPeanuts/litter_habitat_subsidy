# Metadata for the initial mass and organic matter mass data for the leaf litter

## File

    litter_initial_OM.csv
    
## Description

* Collected by: KF and NW

* Collected on 15 Feb 2017

* Affiliation: Longwood University

* Location: Longwood University

## Modified

These data were collected as part of the litter habitat subsidy experiment conducted in the Spring of 2017. 

Details about the experimental set-up can be found in the [litter_habitat_subsidy lab_notebook](https://github.com/KennyPeanuts/litter_habitat_subsidy/blob/master/lab_notebook/habitat_setup_sp2017.md).

The data show the mass of the leaves of the handling controls that were placed into the pond and then immidiately retrieved to get the initial mass.

## Variable Descriptions

* treat = the description of the treatment, where "bag" is the leaf substitue made from paper bags, "Cond" is conditioned leaves collected from the LPP littoral zone, and "UC" is unconditioned leaves collected from LPP shoreline.

* rep = the replicate

* bag.mass = the mass of the empty paper bag used to dry the leaves (g).

* bag.leaf = the dry mass of the leaves and bag (g).

* leaf.whole = the dry mass of the leaves before grinding (g). NOTE: this mass does not include the leaf matter removed for CN analysis.

* cruc = the crucible ID.

* cruc.mass = the mass of the empty crucible (g).

* cruc.leaf = the dry mass of the ground leaves and the crucible (g).

* cruc.ash = the mass of the ash and crucible after 4+ h at 550 dC (g).

* leaf.crush = the dry mass of the ground/crushed leaves (g) NOTE: this mass does not include the leaf material removed for CN analysis.

* ash.mass = the mass of the ash (g).

* AFDM.wo.discs = the ash-free-dry-mass of the leaves not including the matter removed for CN analysis (g).

* prop.OM = the proportion of organic matter in the leaves (LOI-550).

* CN.cruc = the crucible ID for the CN discs

* CN.cruc.mass = the mass of the empty crucible used with the CN discs (g).

* CN.cruc.leaf = the dry mass of the crucible plus the discs for CN analysis (g).

* CN.cruc.ash = the mass of the ash from the CN discs, plus the crucible after 4+ h at 550 dC (g).

* CN.leaf.mass = the dry mass of the discs used for CN (g).

* CN.ash.mass = the mass of the ash from the CN discs (g).

* CN.AFDM.samp = the ash-free-dry-mass of the 10 CN discs per sample (g).

* CN.leaf.num = the number of leaf discs per sample used for CN.

* CN.AFDM.disc = the estimated AFDM of each CN leaf disc (g).

* CN.prop.OM = the proportion of organic matter in the leaf discs in each sample (LOI-550).

* AFDM = the total ash-free-dry-mass of the sample including the leaf matter removed for CN analysis (g).

## Data Entry

    treat <- c(rep("bag", 3), rep("UC", 3), rep("Cond", 3))
    rep <- c(rep(c("A", "B", "C"), 3))
    bag.mass <- c(6.9907, 7.1555, 7.2163, 7.1147, 7.1223, 7.1218, 7.1322, 7.0054, 7.0134)
    bag.leaf <- c(9.4462, 9.2071, 8.9309, 10.8681, 10.7079, 10.4832, 9.9329, 9.8592, 10.0184)
    leaf.whole <- bag.leaf - bag.mass
    cruc <- c(10, 15, 16, "8 & 24", "4 & 13", "5 & 14", "7 & 9", "12 & 17", "20 & 21")
    cruc.mass <- c(29.7499, 26.9922, 28.8752, (28.9696 + 29.4000), (27.4902 + 29.7294), (30.3831 + 28.2208), (28.2010 + 27.0824), (28.1276 + 30.5173), (29.1413 + 31.0044))
    cruc.leaf <- c(31.8913, 28.7506, 30.2983, (31.0404 + 30.6589), (29.2046 + 31.1850), (31.2660 + 30.2924), (29.2073 + 28.4785), (28.7491 + 32.3735), (30.1924 + 32.5747))
    leaf.crush <- cruc.leaf - cruc.mass
    cruc.ash <- c(29.8050, 27.0368, 28.9097, (29.0575 + 29.9537), (27.5606 + 29.7842), (30.4194 + 28.3015), (28.3199 + 27.2182), (28.1837 + 30.6731), (29.2405 + 31.1426))
    ash.mass <- cruc.ash - cruc.mass
    AFDM.wo.discs <- leaf.crush - ash.mass
    prop.OM <- AFDM.wo.discs / leaf.crush
    CN.cruc <- c(4, 6, 10, 5, 9, 7, 11, 8, 12) 
    CN.cruc.mass <- c(12.24, 11.9923, 12.9371, 12.99, 11.6694, 12.1998, 11.89, 12.6025, 11.7836)
    CN.cruc.leaf <- c(12.2682, 12.0144, 12.9588, 13.0218, 11.6955, 12.2269, 11.9174, 12.6330, 11.8114)
    CN.leaf.mass <- CN.cruc.leaf - CN.cruc.mass
    CN.cruc.ash <- c(12.2475, 11.9930, 12.9373, 12.9981, 11.6702, 12.2005, 11.8929, 12.6043, 11.7858)
    CN.ash.mass <- CN.cruc.ash - CN.cruc.mass
    CN.AFDM.samp <- CN.leaf.mass - CN.ash.mass
    CN.leaf.num <- rep(5, 9)
    CN.AFDM.disc <- CN.AFDM.samp / CN.leaf.num
    CN.prop.OM <- (CN.leaf.mass - CN.ash.mass) / CN.leaf.mass
    AFDM <- AFDM.wo.discs + CN.AFDM.samp
    
### Make Data Frame

    leaf <- data.frame(treat, rep, bag.mass, bag.leaf, leaf.whole, cruc, cruc.mass, cruc.leaf, cruc.ash, leaf.crush, ash.mass, AFDM.wo.discs, prop.OM, CN.cruc, CN.cruc.mass, CN.cruc.leaf, CN.cruc.ash, CN.leaf.mass, CN.ash.mass, CN.AFDM.samp, CN.leaf.num, CN.AFDM.disc, CN.prop.OM, AFDM) 

## Write Table

    write.table(leaf, "./data/litter_initial_OM.csv", row.names = F, quote = F, sep = ",")
