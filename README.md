This project will be to move code originally created on SAS to R and potentially other languages.
>It will also serve as a tool to teach other team members about using GitHub.

**Let's Begin!**

To load in an excel sheet, you will need to install and load in a few packages. We will also load in some other packages we will be using for analysis and visualization later on. 

>[!TIP]
>You can use the c() function to list out all the packages you want to install at once but can not do that with library() so we create a vector to use lapply() to solve this!

`install.packages(c("data.table", "readxl", "ggplot2", "dplyr")`
`packages <- c('ggplot2', 'data.table', 'readxl', 'dplyr')`
`lapply(some_packages, library, character.only=TRUE)`

Next, we will grab the EMS Weekly data collection and name it "EMS_test"

 `EMS_test <- as.data.table(read_excel("~/Data_24/EMS_Tableau_Weekly.xlsx", sheet = "EMS_Tableau_Weekly"))`

Loading in CSV files is a _bit easier_ but for excel, you will need to know the name of each sheet you are pulling in. For this example, there is only one!

Next we can do a quick look at the **Average Age** broken down by Year and Gender. 

`EMS_years <- EMS_test %>% group_by(MMWR_Year, Gender) %>% summarise(avg_age = mean(Age, na.rm=TRUE), .groups="drop")`

