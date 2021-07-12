##### WELCOME
# SATYAJIT'S PERSONAL PORTFOLIO




# MORE ABOUT SATYAJIT
- Entry level data analytics professional. Recently completed 6-month of GOOGLE data analytics professional certificate course. Proficient Knowledge in data collection by asking effective questions, preparing data to meet stakeholder’s expectation, working with clean data to gain the right insight, analysing data and making effective data-driven decision. Advanced skill in sharing the insight collected from the analysis to the stakeholder and using R-programming to clean data, plot graph for visualization and statistical analysis.

- According to the DISC Personality model, I have- 63% Dominance.- 14% Compliance.- 12% Influence.- 12% Steadiness. I have a strong inner motivation to assertively create and implement new ideas. I am innovative. I handle pressure well. I strive for excellence and expect others to do the same. 

- I am a Commander (ENTJ) with 70% Extraverted, 66% Intuitive, 69% Thinking, and 91% Judging according to Meyers-Briggs Type Indicator (MBTI) test.

# SQL portfolio project
### Covid 19 global report
Some of my work using structured query language

```markdown
SELECT *
FROM newproject..covid_death
ORDER BY 3,4;



SELECT *
FROM newproject..covidvaccination
ORDER BY 3,4;

SELECT location, date, total_cases,total_deaths, population
FROM Newproject..covid_death
ORDER BY 1,2

--looking at total case vs total death next

SELECT location, date, total_cases, total_deaths, (total_deaths/total_cases) AS death_percentage
FROM Newproject..covid_death
ORDER BY 1,2 ;

--lets convert to percentage to see what is the death percent if you get covid

SELECT location, date, total_cases, total_deaths, (total_deaths/total_cases)* 100 AS death_percentage
FROM Newproject..covid_death
ORDER BY 1,2 ;

--to see covid cases from india

SELECT location, date, total_cases, total_deaths, (total_deaths/total_cases)* 100 AS death_percentage
FROM Newproject..covid_death
WHERE location LIKE 'india%'
ORDER BY 1,2 ;


-- what percentage of population got covid

SELECT location, date, total_cases,total_deaths, (total_cases / population) * 100 AS Percentage_of_cases
FROM Newproject..covid_death
ORDER BY 1,2;

-- -- what percentage of population got covid IN INDIA


SELECT location, date, total_cases,total_deaths, (total_cases / population) * 100 AS Percentage_of_cases
FROM Newproject..covid_death
WHERE location LIKE 'india%'
ORDER BY 1,2;

-- we are looking at the highest percentage of covid cases from all over world

SELECT location, population, MAX(total_cases) AS  HIGHEST_CASE ,MAX((total_cases/population))*100 AS Percentage_of_cases
FROM Newproject..covid_death
GROUP BY location, population
ORDER BY 4 DESC;


-- highest number of death across country

SELECT location, MAX(cast(total_deaths AS int)) AS total_deathcount
FROM Newproject..covid_death
WHERE continent is null
GROUP BY location
ORDER BY total_deathcount DESC;

-- cases across globe

SELECT date, 
SUM(CAST(new_cases AS int)) as totalcase, 
SUM(CAST(new_deaths AS INT)) AS totaldeath, 
SUM(CAST(new_deaths AS INT)) / SUM(new_cases) *100 as death_percentage
FROM Newproject..covid_death
WHERE continent is not null
GROUP BY date
ORDER BY 1,2 ;

-- total death percentage all over the world

SELECT  
SUM(CAST(new_cases AS int)) as totalcase, 
SUM(CAST(new_deaths AS INT)) AS totaldeath, 
SUM(CAST(new_deaths AS INT)) / SUM(new_cases) *100 as death_percentage
FROM Newproject..covid_death
WHERE continent is not null;

SELECT * FROM Newproject..covidvaccination

-- Lets see vaccination details from another table

SELECT * 
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location;


-- LETS SEE TOTAL VACCINATION

SELECT vaccination.location, 
vaccination.date, 
population, 
vaccination.total_vaccinations
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location
WHERE death.continent IS NOT NULL 
order by 1,2,3;

--lets look total vaccination all over india (we can also select a particular country)

SELECT vaccination.location, 
vaccination.date, 
population, 
vaccination.total_vaccinations as vaccination_perday
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location
WHERE death.continent IS NOT NULL 
AND death.location LIKE 'india%'
order by 1,2,3;



-- TO GET MORE CLEAR PICTURE

SELECT vaccination.location, 
vaccination.date, 
population, 
vaccination.total_vaccinations as vaccination_perday
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location
WHERE death.continent IS NOT NULL 
AND death.location LIKE 'india%'
AND vaccination.total_vaccinations IS not null
order by 1,2,3;

-- lets add a windows function

SELECT vaccination.location, 
vaccination.date, 
population, 
vaccination.total_vaccinations as vaccination_perday,
SUM(CAST(vaccination.new_vaccinations AS INT)) OVER(PARTITION BY vaccination.location),
vaccination.total_vaccinations
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location
WHERE death.continent IS NOT NULL 
AND vaccination.total_vaccinations IS not null
order by 1,2,3;



SELECT vaccination.location, 
vaccination.date, 
population, 
vaccination.total_vaccinations as vaccination_perday,
SUM(CAST(vaccination.new_vaccinations AS INT)) OVER(PARTITION BY vaccination.location ORDER BY vaccination.location, vaccination.date),
vaccination.total_vaccinations
FROM Newproject..covid_death  AS death
JOIN Newproject..covidvaccination  AS vaccination
ON death.date = vaccination.date
AND death.location = vaccination.location
WHERE death.continent IS NOT NULL 
AND vaccination.total_vaccinations IS not null
order by 1,2;

```

### R-programing language
My work using R-studio

```markdown

# Vizualizing code using ggplot2


## To create a visualization plot between body_mass_g & bill_depth_mm
## by loading ggplot2 & palmerpenguins package

library(ggplot2)
library(palmerpenguins)
data("penguins")
View(penguins)

ggplot(data= penguins) + geom_point(mapping = aes(x= bill_depth_mm , y= body_mass_g))

## Plot show a positive relationhip between two points
#___________________

## adding a color for a detailed view for better understanding  of different species

ggplot(data = penguins) + geom_point(mapping = aes(x=bill_depth_mm, y = body_mass_g, color= body_mass_g))

## to add a color and shape for more detailed understanding of different species

ggplot(data = penguins) + geom_point(mapping = aes(x=bill_depth_mm, y = body_mass_g, color= species, shape= species))

## now i want to view same data using a line graph plot 
#along with the correlation between the species

ggplot(data = penguins) + 
  geom_smooth(mapping = aes(x=bill_depth_mm, y = body_mass_g, color= species, shape= species)) +
  geom_point(mapping = aes(x=bill_depth_mm, y = body_mass_g, color= species, shape= species))




## now i will work using a bar graph to work with diamonds dataset

ggplot(data = diamonds) + geom_bar(mapping = aes(x=cut))

ggplot(data = diamonds) + geom_bar(mapping = aes(x=cut, color=cut))

## to differenciate the bar chart by color 

ggplot(data = diamonds) + geom_bar(mapping = aes(x=cut, fill = cut))


## to display subset of my data and smaller group
## to create a separate plot for each species

ggplot(data = penguins)+
  geom_point(mapping=aes(x=bill_depth_mm, y = body_mass_g))+
  facet_wrap(~species)

## to create a separate plot for each species and add a color to differenciate the plots

ggplot(data=penguins, aes(x=bill_depth_mm, y= body_mass_g))+
  geom_point(aes(color= species))+
  facet_wrap(~species)

```
## Using R programing to understand DATA FRAME

```markdown

## Data frame
## as an data analyst having proper knowledge about data frame is imp.

#we need to instal ggplot2 package 

install.packages("ggplot2")
library("ggplot2")
data("diamonds")
View(diamonds)

## diamonds dataframe has 53940 rows and 10 variables

## -------------------------------------------------------------

## But i want to view only the first 6 columns from the data frame
## so i have to use head() function

head(diamonds)

## now i want to summarize the data frame to collect some more insights
## to view only the column names by using colnames() function

colnames(diamonds)


# now i want to clean my data frame
## for which ineed to install (here, skimr, janitor, dplyr) functions

install.packages("here")
library(here)

install.packages("skimr")
library(skimr)

install.packages("janitor")
library(janitor)

install.packages("dplyr")
library(dplyr)

```

[IMAGE](C:\Users\18080\Downloads)

# CONTACT DETAILS

##### (*Contact satyajit on 8249538484*)
##### (*E-mail satyajit on 1808037@kiit.ac.in  or  sarangisatya2017@gmail.com*)
This link will directly take you to satyajits linkedin profile [linkedin link](https://www.linkedin.com/in/satyajit-sarangi-38515a206/).
My work on Visual representation using [Tableau](https://public.tableau.com/profile/satyajit.sarangi#!/?newProfile=&activeTab=0) to communicate my findings to stakeholders.
