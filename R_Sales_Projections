#call libraries 
library(prophet) 
library(dplyr) 

# read in data frame. (possibly add in more historical data)
#df <- read.csv('C:\\Users\\ablan\\OneDrive - Company\\Desktop\\sales projection input data.csv')

#convert date column to date format
#df$Date = as.Date(df$Date, format = "%d - %m - %y")

#convert column names to be compatible with prophet 
colnames(df9) = c('ds','y')

# TO Do -- take out outliers
outliers <- (as.Date(df9$ds) > as.Date('2020-03-08')
             & as.Date(df9$ds) < as.Date('2020-06-28')
             & as.Date(df9$ds) < as.Date('2020-03-15')
             & as.Date(df9$ds) < as.Date('2019-06-30')
         )
df9$y[outliers] = NA

#add superbowl to holidays. Is it necessary to add playoffs? 
superbowl <- data_frame( 
  holiday = 'superbowl', 
  ds = as.Date(c('2015-02-01','2016-02-07','2017-02-05', 
                 '2018-02-05','2019-02-03','2020-02-02', 
                 '2021-02-07')) 
) 
#add superbowl as a holiday to help lags 
holidays <- bind_rows(superbowl) 

#call prophet function with parameters adjusted 
m <- prophet(holidays = holidays 
             , changepoint.range = 0.66 
             , changepoint.prior.scale = 1
             , weekly.seasonality = 3 
             , yearly.seasonality = 22
             
) 

#add custom seasonality 
m <- add_seasonality(m, name='monthly', period=30.5, fourier.order=7) 

#built in holidays 
m <- add_country_holidays(m,country_name = 'US') 

#fit the model with the historical data 
m <- fit.prophet(m,df9) 

#create future dataframe for x periods 
future <- make_future_dataframe(m, periods = 52, freq = 'week') 

#look at the last predicted dates (ds column) 
#tail(future) 

#predict future values using the dataframe
future <- predict(m, future)

# plot of the potential changepoints
plot(m, future) + add_changepoints_to_plot(m)

#see the trend, holidays, weekly, yearly and monthly plots
prophet_plot_components(m,future)

#interactive plot of actuals vs predictions
dyplot.prophet(m,future)

library("writexl") 
# export file to excel.
write_xlsx(future,"C:\\Users\\ablan\\OneDrive - Company\\Work\\Salty and Bev\\forecast.xlsx")  

