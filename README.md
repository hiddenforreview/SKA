# TC for SKA
Anonymous repository for Semi-Supervised Knowledge Amalgamation for Sequence Classification via Teacher Coordinator (TC) 

## File listing

+ __model.py__ The main code implementation of TC
+ __main.py__ Code for training TC
+ __utils.py__ All supporting functions

## Instructions on training TCom

Run script as:

  python main.py -expname 'test' -t_model ./teachers/t1.sav ./teachers/t2.sav -t_numclass 3 3 -t_class 0 1 2 3 2 3 4 5 -s_class 0 1 2 3 4 5 -data ./data/syn_test.txt 
  
%data_label ./data/labeled_data.txt -data_unlabel ./data/unlabeled_data.txt -expname 'test'
  
Required parameters:

+ __-t_model__ a list of paths of teacher models 
+ __-t_numclass__ the number of classes corresponding to t_model
+ __-t_class__ a list of specialized classes of each teacher, concatenated in correspond to t_model , e.g., t1_class: 0 1 2 3 and t2_class: 2 3 4 5, then t_class: 0 1 2 3 2 3 4 5
+ __-s_class__ a list of comprehensive classes of the student
+ __-data_label__ the student training data file with labels
+ __-data_unlabel__ the student training data file with no label
+ __-expname__ experiment name

Parameters:
+ __-lr__ learning rate, default 0.001
+ __-ep__ epochs, default 200
+ __-bs__ batch size, default 8
+ __-layers__ #layers, default 2
+ __-hiddim__ #hidden units, default 8
+ __-inputsize__ #features, default 1
+ __--save__ boolean parameters, whether to save the student model, default false
