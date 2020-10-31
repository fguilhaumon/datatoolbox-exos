---
title: "Manipulation de données avec {dplyr}"
author: "francois.guilhaumon@ird.fr"
date: "04/11/2020"
output:
  html_document:
    keep_md: yes
---



# Introduction

Dans cet exercice nous allons utiliser le package `dplyr` pour nous instruire sur la biogéographie des ours.

# Données

On utilise la base [**WWF Wildfinder**](https://www.worldwildlife.org/pages/wildfinder-database)

La base de données WildFinder du WWF contient des données de présence/absence pour les amphibiens, reptiles, oiseaux et mammifères terrestres du monde entier au niveau des écorégions terrestres. Seul le sous-ensemble des mammifères est disponible dans ce dépôt avec 4936 espèces. Les données, préalablement nettoyées, sont structurées de la manière suivante dans le dossier `data/wwf-wildfinder/` :

  - `wildfinder-mammals_list.csv` : liste taxonomique des 4936 espèces de mammifères du monde entier
  - `wildfinder-ecoregions_list.csv` : liste des 798 écorégions terrestres définies par le WWF
  - `wildfinder-ecoregions_species.csv` : correspondances entre les espèces et les écorégions

## Analyses

### Exploration des données

- Histogramme de la distribution du nombre d'espèces de mammifères par écorégion.


```r
#read wildfinder-ecoregions_species.csv
sp_eco <- datatoolboxexos::data_sp_eco()
```

```
## 
## ── Column specification ────────────────────────────────────────────────────────
## cols(
##   ecoregion_id = col_character(),
##   species_id = col_double()
## )
```

```r
#tabulate the ecoregions
mam_per_eco <- table(sp_eco$ecoregion_id)

#histogram
hist(mam_per_eco,
     main = "Number of mammal species per ecoregion",
     breaks = 50
)
```

![](exo_dplyr_files/figure-html/explo_histo-1.png)<!-- -->
