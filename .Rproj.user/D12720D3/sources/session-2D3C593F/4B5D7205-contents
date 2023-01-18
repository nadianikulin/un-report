#read in data and create column names
co2_data_dirty<-read_csv("co2-un-data.csv" , skip=2,
                   col_names = c("region", "country", "year", "series", "value", "footnotes", "source"))
#info on read function
?read_csv

#create new column names 
co2_data_2005<-co2_data_dirty %>% 
  select(country, year, series, value) %>%
  mutate(series= recode(series, "Emissions (thousand metric tons of carbon dioxide)" = "total_emissions", 
                        "Emissions per capita (metric tons of carbon dioxide)" = "per_capita_emissions"))%>%
  pivot_wider(names_from = series, values_from = value) %>% 
  #want to combine emissions data for a specific country in a given year which is joining data
filter(year=="2005") %>% 
select(-year)


# bringing in 2007 population data
gapminder_data_2007 <-read_csv("data/gapminder_data.csv") %>% 
  filter(year== 2007) %>% 
  select(country, pop, lifeExp, gdpPercap)

# countries that share data in separate tables to be combined into one table so order doesn't matter
joined_co2_pop<-inner_join(co2_data_2005, gapminder_data_2007, by = "country")
# countries that are missing data in a table so order matters since first table is a filter
anti_join(gapminder_data_2007, co2_data_2005, by = "country")
# countries with data or without. NA implies no data
full_join(co2_data_2005, gapminder_data_2007)
# bring in data from gapminder without losing any data from co2
co2_data_2005%>%
  left_join(gapminder_data_2007)

# writing an object to csv
write_csv(joined_co2_pop, file = "data/joined_co2_pop.csv")

#read back in the csv file written above
joined_co2_pop<-read_csv("data/joined_co2_pop.csv")

#plotting data in ggplot
joined_co2_pop%>% 
ggplot(aes(x=gdpPercap)) +
  geom_histogram()

# plotting gdpPercap x axis and co2 emissions on the y
gdp_co2_plot<-joined_co2_pop%>%
  ggplot(aes(x= gdpPercap, y= per_capita_emissions))+
  geom_point()+
  geom_smooth(method= "lm", se= FALSE)+
  labs(x= "GDP Per Capita", y= "CO2 Emmissions Per Capita (metric tons)", title= "Comparing CO2 Emissions and GDP Per Capita")+
  theme_classic()+
  ggpubr::stat_regline_equation(aes(label= after_stat(rr.label)))

ggsave(gdp_co2_plot, filename = "figures/gdp_vs_co2_plot.png", height= 4, width= 6, units= "in", dpi= 300)


install.packages("ggpubr")
