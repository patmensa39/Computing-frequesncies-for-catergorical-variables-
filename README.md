# Computing-frequesncies-for-catergorical-variables-
#COMPUTING FREQUENCIES ###
### Loading the libraries ###
pacman::p_load(pacman, rio, tidyverse)

### loading and preparing the dataset (Google search data)
### Selecting only the catergorical variables 
data<- import("StateData.xlsx") %>% as_tibble() %>% 
       select(state_code,psychRegions,region) %>% 
      mutate(psychRegions = as.factor(psychRegions))
view(data)

### Summarizing the dataframe 
summary(data) # This gives frequencies of factors only 

### Another way is to do the same thing using piping 
data %>% summary()
### You realized psychRegion showed factors because I made it as factors 

## Summarizing the catergorical variables 
### Summary is not really useful in catergorical variables
### Remember region is a character variables
data %>% select(region) %>% summary() # not quite useful 

### Using table 
data %>% select(region) %>% table() # this works better 

## Summarizing factor variables 
### Using summary()
### Because these were made as.factors when importing the data, summary works well 
### Remember psychRegion is a factor variable 
data %>% select(psychRegions) %>% summary() # works better

### Using table ()
data %>% select(psychRegions) %>% table() # its ok but makes it longer 

### Summarizing multiple factor.
### With these, I have to make all the catergorical variables as.factors 
data2 <- data %>% mutate(region = as.factor(region)) %>% 
                  mutate(psychRegions = as.factor(psychRegions)) %>% 
                  print(n = Inf) # n = Inf means show all the observations 
view(data2)

### After these, you can use summary()
summary(data2) # perfect 






