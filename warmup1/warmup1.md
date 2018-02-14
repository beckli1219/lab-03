---
title: "Lab2"
author: "Yuanrong Li"
date: "2018/2/1"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

```{r}
load('nba2017-salary-points.RData')
```

```{r}
length( player)
length( points)
length( position)
length( salary)
length( team)
```

```{r}
head(player)
head(points)
head(position)
head(salary)
head(team)
```

```{r}
tail(player)
tail(points)
tail(position)
tail(salary)
tail(team)
```

```{r}
summary(player)
summary(points)
summary(position)
summary(salary)
summary(team)
```

```{r}
#class of each of the objects
class(player)
class(points)
class(position)
class(salary)
class(team)
```

```{r}
#How do you know if any of the loaded objects is a vector?
str(player)
str(points)
str(position)
str(salary)
str(team)
```

```{r}
#How do you know that a given vector is of a certain data type?
mode(player)
mode(points)
mode(position)
mode(salary)
mode(team)
```


```{r}
#all the even elements in player
player[ seq( 2, length( player) , 2 )]
#all the odd elements in salary
salary[ seq(1, length(salary) , 2)]
#all multiples of 5 (e.g. 5, 10, 15, etc) of team
team[seq(5, length(team), 5)]
#elements in positions 10, 20, 30, 40, etc of scored
points[ seq(10, length(points) , 10)]
#all the even elements in team but this time in reverse order
team[seq(440, 1, -2)]
```

```{r}
#players in position Center, of Warriors (GSW)
player[team == 'GSW' & position == "C"]
```

```{r}
#players of both GSW (warriors) and LAL (lakers)
player[team == "GSW" | team == "LAL"]
```

```{r}
#players in positions Shooting Guard and Point Guards, of Lakers (LAL)
player[ team == "LAL" & position == "SG" & position == "PG"]
```

```{r}
#subset Small Forwards of GSW and LAL
player[ (team == "GSW" & position == "SF") | (team == "LAL" & position == "SF") ]
```

```{r}
#name of the player with largest salary
player[ which.max(salary)]
#name of the player with smallest salary
player[which.min(salary)]
#name of the player with largest number of scored points
player[which.max(points)]
#salary of the player with largest number of points
salary[which.max(points)]
#largest salary of all Centers
max(salary[ position == "C"])
#team of the player with the largest number of scored points
team[which.max(points)]
#name of the player with the largest number of 3-pointers
player[which.max(points3)]
```


```{r}
warriors_player <- player[ team == 'GSW']
warriors_salary <- salary[ team == 'GSW']
warriors_points <- points[ team == 'GSW']
names(warriors_salary) <- warriors_player
warriors_salary["Andre Iguodala"]
warriors_salary[c("Stephen Curry", "Kevin Durant")]
```

```{r}
plot(points, salary) 
log_scored <- log(points)
log_salary <- log(salary)
plot(log_scored, log_salary)
text(log_scored, log_salary, labels = abbreviate(player))
```

```{r}
#create a scatterplot of points and salary for the Warriors (GSW), displaying the names of the players. Generate two scatterplots, one with raw values (original scale, and another plot with log-transformations)
plot(warriors_points, warriors_salary)
text(warriors_points, warriors_salary, labels = abbreviate(warriors_player))
log_warriors_scored <- log(warriors_points)
log_warriors_salary <- log(warriors_salary)
plot(log_warriors_scored , log_warriors_salary)
text(log_warriors_scored , log_warriors_salary, labels = warriors_player)
```


```{r}
salary_millions <- 1/1000000 * salary
scored_points <- points1 + points2 *2 + points3 *3
position_fac <- factor(position)
table(position_fac)
#positions of Warriors
position_fac[ team == "GSW"]
#positions of players with salaries > 15 millions
position_fac[ salary_millions > 15]
#frequencies (counts) of positions with salaries > 15 millions
table(position_fac[ salary_millions > 15])
#relative frequencies (proportions) of 'SG' (Shooting Guards) in each team
team_fac <- factor(team)
table(team_fac[ position == "SG"]) / 95
```

```{r}
plot(points, salary , col = position_fac , pch = 1, cex =1)
```













