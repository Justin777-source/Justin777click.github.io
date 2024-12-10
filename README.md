Analyzing The Density of Non-Native vs Native Urban Tree Species 

By Justin Harris 







In this project, I am looking at the most common species of trees in urban areas and determining if there are more native tree or introduced species within each city.
The cities I am collecting data from are Seattle and New Orleans. I chose these regions as they represent each geographical region of the U.S.
My objective in this project is to determine if urbanization increases or decreases tree native species diversity. Or do certain tree species do better in urban environments than others? 
 

**Data:** 

The dataset I used came from the Dryad dataset of 5 million trees, describing their nativity, health, and location within 63 U.S cities. 


**Methods **

The code I employed for this operation  was:

New Orleans 


tree_data <- read.csv("C:/Users/Justi/Downloads/doi_10_5061_dryad_2jm63xsrf__v20220830/NewOrleans_Final_2022-06-18.csv")

native_trees <- tree_data %>% 
  filter(native == "native")

area_new_orleans_km2 <- 906

tree_data$native <- tolower(trims(tree_data$native))

**Group BY**

tree_density <- tree_data %>%
  group_by(native) %>%
  summarise(count = n()) %>%
  mutate(density = count / area_new_orleans_km2)

print(tree_density)

**GGPLOT**

ggplot2(tree_density, aes(x = native, y = density, fill = native)) +
  geom_bar(stat = "identity", show.legend = FALSE) +
  theme_minimal() +
  labs(
    title = "Density of Tree Species in New Orleans by Native Status",
    x = "Native Status",
    y = "Tree Density (trees/km²)"
  ) +
  scale_fill_manual(values = c("introduced" = "red", 
                               "naturally_occurring" = "green", 
                               "no_info" = "gray"))

Seattle

tree_data2<-read.csv("C:/Users/Justi/Downloads/doi_10_5061_dryad_2jm63xsrf__v20220830/Seattle_Final_2022-06-18.csv")

native_trees2 <- tree_data2 %>% 
  filter(native == "native")

area_seattle_km2 <- 142.5

tree_data2$native <- (tolower(trimws(tree_data2$native))

tree_density2 <- tree_data2 %>%
  group_by(native) %>%
  summarise(count = n() %>%
  mutate(density = count / area_seattle_km2)

ggplot2(tree_density2, aes(x = native, y = density, fill = native)) +
  geom_bar<-(stat = "identity", show.legend = FALSE) +
  theme_minimal() +
  labs(
    title = "Density of Tree Species in Seattle by Native Status",
    x = "Native Status",
    y = "Tree Density (trees/km²)"
  ) +
  scale_fill_manual(values = c("introduced" = "blue", 
                               "naturally_occurring" = "green", 
                               "no_info" = "gray"))






results:

New Orleans Density


  native              count density
  <chr>               <int>   <dbl>
1 introduced          52821   58.3 
2 naturally_occurring 48151   53.1 
3 no_info              4841    5.34

![Image](https://github.com/user-attachments/assets/59dd55f8-d329-4a42-a1c3-a2a19c22f7a9)


Seattle Density
<html>
<body>
<!--StartFragment-->
1 | introduced | 
 121176 |
 850.35789
-- | -- | -- | --
2 | naturally_occurring |
 9887 | 69.38246
3 | no_info |
 34560 | 242.52632

<!--EndFragment-->
</body>
</html>

![Image](https://github.com/user-attachments/assets/d2a371de-acb9-41d0-b7df-1c059a460be5)
