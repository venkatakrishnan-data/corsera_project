# corsera_project
I have did the the prediction using SVM machine learning algorith.
getwd()
setwd("E:")
proo1<-read.csv("E:/Rcorsera/pml.csv")



pro1<-subset(proo1, select=c(user_name,raw_timestamp_part_1,
                                raw_timestamp_part_2,
                                new_window,num_window,roll_belt,
                                pitch_belt,yaw_belt,total_accel_belt,gyros_belt_x,
                                gyros_belt_y,gyros_belt_z,accel_belt_x,accel_belt_y,
                                accel_belt_z,magnet_belt_x,magnet_belt_y,
                             
                             magnet_belt_z,roll_arm,pitch_arm,yaw_arm,total_accel_arm,
                             roll_dumbbell,pitch_dumbbell,yaw_dumbbell,gyros_dumbbell_x
                             ,gyros_dumbbell_y,gyros_dumbbell_z,accel_dumbbell_x,
                             accel_dumbbell_y,accel_dumbbell_z,magnet_dumbbell_x,
                             magnet_dumbbell_y,magnet_dumbbell_z,roll_forearm,
                             pitch_forearm,yaw_forearm,gyros_forearm_x,
                             gyros_forearm_y,gyros_forearm_z,accel_forearm_x,
                             accel_forearm_y,accel_forearm_z,magnet_forearm_x,
                             magnet_forearm_y,magnet_forearm_z,
                                classe
                     ))
dim(pro1)
train<-subset(pro1[1:19622,])
tail(train,n=20)
test<-subset(pro1[19623:19642,])
pro1$classe<-factor(pro1$classe)
pro2$classe<-factor(pro2$classe)
str(pro2)
svm_model <- svm(classe ~ ., data=train)
summary(svm_model)
trained_out <-predict(svm_model,train,type="C-classification")
tested_out <-predict(svm_model,test,type="C-classification")
write.csv(tested_out,"my_output.csv")



#The data has been joined together as they produce error when loaded seperately and tested in the algorithm. Thats due to the creation of new table while testing the data with the training set  

#RESULT :confusion matrics for the train sample with SVM model.  
                    A    B    C    D    E
               0    0    0    0    0    0
          A    0 5481  249   14   13    0
          B    0   31 3417  138    0   22
          C    0   42   96 3197  253   65
          D    0   25   13   49 2944   63
          E    0    1   22   24    6 3457

RESULT: output produced for the TEST set.
	x
1	B
2	A
3	A
4	A
5	A
6	E
7	D
8	B
9	A
10	A
11	B
12	C
13	B
14	A
15	E
16	E
17	A
18	B
19	B
20	B
