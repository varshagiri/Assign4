##### We load in libraries
`
library(ggplot2) 
library(plotly)
`
##### We Change Directory
`
setwd('~/mygraph2/bin/')
`
##### We load in our dataframe
`
mygenes <- read.csv('gene_dist_head.tsv', header= TRUE, sep = "\t",fill = TRUE) 
`
### We define a factor set of autosomes
`
 autosomes<-c("1","2","3","4","5","6","7","8","9","10",
 "11","12","13","14","15","16","17","18","19","20","21","22")  
`
### We create a new dataframe called 'genes' which only has autosomes, however we still have those additional factors
`
 genes<- mygenes[ which(mygenes$chr %in% autosomes), ] 
`
### We remove the factors and then order them so they are numerical order and not alphabetical
`
 genes$chr <- factor(genes$chr, levels = autosomes) 
`
### We plot in ggplot 
`
ggplot(data = genes) +  geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
`
`
ggplot(data = genes) + geom_bar(mapping = aes(x = feature))
`
`
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature))
`
`
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1) + coord_polar()
`
### Install devtools into the library
`
 install.packages("devtools")
`
`
 devtools::install_github('hadley/ggplot2')
`
### To plot polar coordinates 
`
 p<-ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
`
### To have plotly work on the graph
`
 ggplotly(p) 
`

###### Now we see tooltips
