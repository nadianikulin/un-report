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

#countries that share data in separate tables to be combined into one table so order doesn't matter
inner_join(co2_data_2005, gapminder_data_2007, by = "country")
#countries that are missing data in a table so order matters since first table is a filter
anti_join(gapminder_data_2007, co2_data_2005, by = "country")
#countries with data or without. NA implies no data
full_join(co2_data_2005, gapminder_data_2007)
