# Logistic-Regression-with-R
# Build a binary logistic regression model to predict store type given certain transaction characteristics.
# Specifically predict the probability of store_type is ‘C’ or not given certain characteristics

##### 1. LOAD LIBRARIES #####
library(sqldf)
library(zoo)
library(lubridate)
library(pROC)

#####2.LOAD DATA #####
ross.sales <- read.csv('D:/Personal/Ancile/Training/Batch 1/Class 11 - R Training/Rossmann data/rossmann_sales.csv',stringsAsFactors = F)
store.att  <- read.csv('D:/Personal/Ancile/Training/Batch 1/Class 11 - R Training/Rossmann data/store_attributes.csv',stringsAsFactors = F)


data <- sqldf("SELECT A.*,StoreType FROM `ross.sales` A LEFT JOIN `store.att` B ON A.store = B.Store")

#####3.PREPARE DATA #####
data$date = as.Date(data$date,format = '%m/%d/%Y')
data$year = year(data$date)
data$StoreType = ifelse(data$StoreType=='c',1,0)


data$open = as.factor(data$open)
data$promo = as.factor(data$promo)
data$StoreType = as.factor(data$StoreType)


#####4.CREATE TRAIN/TEST #####
train = subset(data,data$year %in% c(2013,2014),select=c(StoreType,customers,open,promo))
test  = subset(data,data$year %in% c(2015),select=c(StoreType,customers,open,promo))
rm(ross.sales,store.att,data)

#####5.BUILD LOGISTIC REGRESSION #####
model <- glm(StoreType ~.,data = train, family = binomial)
summary(model)


#####6.PREDICT #####
test$prob <- predict(model,type='response', newdata = test)

#Check Plots
# "AUC", "Precision/Recall"
# Load the pROC package

ROC <- roc(test$StoreType, test$prob)
plot(ROC, col = "blue")

# Calculate the area under the curve (AUC)
auc(ROC)


