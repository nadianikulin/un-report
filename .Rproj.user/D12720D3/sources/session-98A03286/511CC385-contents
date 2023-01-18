
# Run life expectancy and CO2 emissions versus population with gapminder
# Date: Jan 17th, 2023
# Author: Marian Schmidt 

# load in packages necessary for analysis
library("tidyverse")
library("readr")
library("ggprism")

# read in data for analysis

gapminder_1997 <- read_csv("gapminder_1997.csv")
read_csv()
read_csv("gapminder_1997.csv")

# learning object order importance
Sys.Date()
getwd()
sum(5,6)
?round
round(3.1415)
round(3.1415,3)
round(x= 3.1415)
round(x= 3.1415, digits =2 )
round(digits= 2, x= 3.1415)
round(2, 3.1415)

# plotting data for visualization
# make skeleton
ggplot(data = gapminder_1997, 
       aes(x = gdpPercap, y= lifeExp, color= continent,
           shape = continent, size = pop)) +
  labs(x= "GDP Per Capita", y= "Life Expectancy",
       title= "Do people in wealthy countries live longer?",
       size= "Population (in millions)") +
  geom_point()

# Read in all of the data from gapminder (more years than 1997)
gapminder_data <- read_csv("gapminder_data.csv")
         
View(gapminder_data) 
dim(gapminder_data)
head(gapminder_data)
tail(gapminder_data)

# viewing the data you are using for plotting geom_line is line plot, geom_point is points
View(gapminder_1997)

ggplot(data = gapminder_data) +
  aes(x=year, y=lifeExp, color=continent, group= country) +
  geom_line()

# learn about data using structure command str which is similar to clicking blue arrow in environment
str(gapminder_data)

# make a box plot for continent on x-axis and life expectancy on y-axis
ggplot(data = gapminder_data) +
  aes(x=continent, y=lifeExp) +
  geom_boxplot()

# make a violin plot same as above
ggplot(data = gapminder_data) +
  aes(x=continent, y=lifeExp) +
  geom_violin()

# add points on top of plot
ggplot(data = gapminder_data) +
  aes(x=continent, y=lifeExp) +
  geom_violin() +
  geom_point()

# all points
ggplot(data = gapminder_data) +
  aes(x=continent, y=lifeExp, color= continent) +
  geom_violin() +
  geom_jitter(aes(size=pop))


# make a histogram
ggplot(gapminder_1997) +
  aes(x=lifeExp, fill= continent) +
  geom_histogram(bins= 20) +
  theme_prism()

install.packages("ggthemes")
install.packages("ggprism")

ggplot(gapminder_1997) +
  aes(x= gdpPercap, y= lifeExp, color= continent) +
  geom_point() +
  facet_grid(rows=vars(continent))

ggsave("figures/awesome_plot.jpg", device= jpg, width = 6, height = 4, 
units= "in")
?ggsave

