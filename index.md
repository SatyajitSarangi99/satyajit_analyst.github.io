##### WELCOME
# SATYAJIT'S PERSONAL PORTFOLIO
##### (*Contact satyajit on 8249538484*)
##### (*E-mail satyajit on 1808037@kiit.ac.in & sarangisatya2017@gmail.com*)
This link will directly take you to satyajits linkedin profile [linkedin link](https://www.linkedin.com/in/satyajit-sarangi-38515a206/).

My work on Visual representation using [Tableau](https://public.tableau.com/profile/satyajit.sarangi#!/?newProfile=&activeTab=0) to communicate my findings to stakeholders.




### SQL
Some of my work using structured query language

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

### R-programing language
My work using R-studio

```markdown
Syntax highlighted code block

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

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```


For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/SatyajitSarangi99/satyajit_analyst.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
