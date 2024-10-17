# rcicr

This package contains functions needed for conducting reverse correlation image classification experiments in psychology (generating stimuli and classification images).

We would very much welcome any contributions, thoughts and criticisms you might have! Please submit an issue at [here](https://github.com/rdotsch/rcicr/issues/){.uri}.

## Install the latest stable version

``` r
install.packages('rcicr')
```

## Install the latest dev version from github

``` r
install.packages('devtools')
devtools::install_github('rdotsch/rcicr')
```

## Using the package

See [this medium post](https://medium.com/@rondotsch/reverse-correlation-image-classification-using-r-a0701648fb0/) which showcases how to use the rcicr package.

## Examples and datasets

See [this github repository](https://github.com/rdotsch/rcicr_examples/).



## 대상의 정보에 따른 정신적 표상
```
ci <- generateCI2IFC(rcdata$stim, rcdata$response, "male", 'stimuli/rcic_seed_1_time_Aug_08_2024_03_37.Rdata', scaling='matched')

ci1 <- generateCI2IFC(rcdata$stim, rcdata$response, 'male', 'stimuli/rcic_seed_1_time_Aug_08_2024_03_37.Rdata', scaling='matched') ci2 <- generateCI2IFC(rcdata$stim, rcdata$response, 'female', 'stimuli/rcic_seed_1_time_Aug_08_2024_03_37.Rdata') cis <- list('male'=ci1, 'female'=ci2) scaled_cis <- autoscale(cis, saveasjpegs = TRUE)

ci <- generateCI2IFC(rcdatas$stim, rcdatas$response, 'female', 'stimuli/rcic_seed_1_time_Aug_10_2024_22_19.Rdata', scaling='matched')

infoVal <- computeInfoVal2IFC(ci1, rdatas)


ci1 <- generateCI(rcdatas$stim, rcdatas$response, 'male', 'stimuli/preconf_seed_1_time_Aug_08_2024_04_29.Rdata', zmap = TRUE, zmapmethod = "t.test")
ci <- generateCI2IFC(rcdatas$stim, rcdatas$response, 'male', 'stimuli/preconf_seed_1_time_Aug_08_2024_04_29.Rdata', scaling='matched')



##############################
## (시작 )
install.packages(“devtools”) 
devtools::install_github(“rdotsch/rcicr”, ref = “development”)
library(rcicr)
install.packages("stringr")

##base_face_files <- list('female'='female.jpg')

generateStimuli2IFC(list(base="baseimage_20240901/512_baseimage_male.jpg"), n_trials = 300)
generateStimuli2IFC(list(base="K_M_02.jpg"), n_trials = 20)

generateStimuli2IFC(list(base="examplekoreanfemaleone.jpg"), n_trials = 10)

rcdata <- read.csv('rcic_20240823_222732.csv', fileEncoding = "UTF-8")
rcdata$stim <- rcdata$trial + 1


rcdata$oriinv <- str_match(rcdata$selectedstim, "_([invori]+).")[,2]

rcdata$response[rcdata$oriinv == 'ori'] <- 1
rcdata$response[rcdata$oriinv == 'inv'] <- -1

## ci <- generateCI2IFC(rcdata$stim, rcdata$response, "base", 'stimuli/rcic_seed_1_time_Aug_10_2024_22_37.Rdata', scaling='matched')

ci1 <- generateCI(rcdata$stim, rcdata$response, "base", 'stimuli/rcic_seed_1_time_Aug_20_2024_11_26.Rdata', zmap = TRUE, zmapmethod = "t.test")
## 위 코드로 진행해야 zmap 에 파일이 생깁니다 


infoVal <- computeInfoVal2IFC(ci1, 'stimuli/rcic_seed_1_time_Aug_20_2024_11_26.Rdata')



## (끝)
###########################

infoVal <- computeInfoVal2IFC(ci1, 'stimuli/preconf_seed_1_time_Aug_08_2024_04_29.Rdata')



file_path <- "C:/Users/circl/OneDrive/바탕 화면/reverse correlation/base_face_files/"
base_face_files <- list(aName = paste0(file_path, 'K_M_01.jpg'))
generateStimuli2IFC(base_face_files, n_trials = 300)
```
