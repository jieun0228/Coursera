# Getting adn cleaning data
## Lecture01

setwd("")

library(XML)
fileUrl <- "http://www.w3schools.com/xml/simple.xml"
doc <- xmlTreeParse(fileUrl, useInternal=TRUE)
rootNode <- xmlRoot(doc)
xmlName(rootNode)
xpathSApply(rootNode, "//name", xmlValue)
xpathSApply(rootNode, "//price", xmlValue)

fileUrl <- "http://espn.go.com/nfl/team/_/name/bal/baltimore-ravens"
doc <- htmlTreeParse(fileUrl, useInternal=TRUE)

scores <- xpathSApply(doc, "//li[@class='score']", xmlValue)
teams <- xpathSApply(doc, "//li[@class='team-name']", xmlValue)


jsonData <- fromJSON("https://api.github.com/users/jtleek")
names(jsonData)

myjson <- toJSON(iris, pretty=TRUE)
iris2 <- fromJSON(myjson)


* data.table inherets from data.frame
library(data.table)
DF = data.frame(x=rnorm(9), y=rep(c("a","b","c"), each=3), z=rnorm(9))
DT = data.table(x=rnorm(9), y=rep(c("a","b","c"), each=3), z=rnorm(9))
DT[2,]
DT[DT$y=="a",]
DT[C(2,3)]

{
  x = 1
  y = 2
}

k={print(10);5}

DT[, m:={tmp <- (x+z); log2(tmp+5)}]
DT[, b:=mean(x+2), by=a]

set.seed(123);
DT <- data.table(x=sample(letters[1:3], 1E5, TRUE))
DT[, .N, by=x] # count(*) group by x

DT <- data.table(x=rep(c("a", "b", "c"), each=300), y=rnorm(300)) 
setkey(DT,x)
DT['a']

DT1 <- data.table(x=c('a', 'a', 'b', 'dt1'), y=1:4)
DT2 <- data.table(x=c('a', 'b', 'dt2'), z=5:7)
setkey[DT1, x]; setkey[DT2, x]
