# Camille Karski 

## Data scientist at Sydney University 

Interested in: 

* Data Science 
* Suststainability 
* Ethics
* All things stats 
* Cats (and dogs!) 

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
knitr::opts_knit$set(root.dir = '/Users/camillekarski/Documents/Uni/DATA3888')

library(class)
library(cvTools)
library(randomForest)
library(tidyverse)
library(tuneR)
library(devtools)
library(ggplot2)
library(tsfeatures)
library(data.table)
library(R.utils)
library(limma)
library(dplyr)

#pretty tables
library(kableExtra)

# Bio Data
library(BiocManager)
library(GEOquery) 
library(Biobase)
library(DT)
library(preprocessCore)

# Maps visualization
library(maps)
library(reshape2)
library(viridis)
library(plotly)
```
```{r}
#reading in short files
dir_short = "DATA3888_data/Spiker_box_Louis/Short"
all_files_short = list.files(dir_short)

wave_file_short = list()
for (i in all_files_short) {
  wave_file_short[[i]] = readWave(file.path(dir_short, i))
}
plot_waves = function(wave_file_dir){
  num = 1
  for (i in wave_file_dir) {
  waveSeq = i
  timeSeq = seq_len(length(waveSeq))/waveSeq@samp.rate 
  plot(timeSeq, waveSeq@left, type = "l", ylab="Signal", xlab="Time(seconds)", 
       main=names(wave_file_dir)[num], sub=num)
  num = num+1
  } #end for
} #end function
plot_waves(wave_file_short)
```
